<template>
  <v-card v-if="selectedCity !== ''" width="800">
    <v-card-text>
      <v-card-title>{{ selectedCity }}</v-card-title>
      <p>Temp: {{ Math.floor(city.temp) }}</p>
      <p>Humidity: {{ city.hum }}</p>
      <p>Description: {{ city.description }}</p>
    </v-card-text>
  </v-card>
</template>

<script>
import store from "../assets/store";

export default {
  data() {
    return {
      city: {
        temp: "",
        hum: "",
        description: "",
      },
    };
  },
  computed: {
    selectedCity: {
      get() {
        return store.selectedCity;
      },

      set(newArray) {
        store.selectedCity = newArray;
      },
    },
  },
  methods: {
    // getData() {
    //   fetch(
    //     `https://api.openweathermap.org/data/2.5/weather?q=${this.selectedCity}&units=metric&appid=a015a19f3f4cf8e896217cbd4eea6eb6`
    //   )
    //     .then((response) => response.json())
    //     .then((weather) => {
    //       console.log(weather);
    //       this.city.temp = weather.main.temp;
    //       this.city.hum = weather.main.humidity;
    //       this.city.description = weather.weather[0].description;
    //     })
    //     .catch((error) => console.log("error", error));
    // },
  },
  watch: {
    selectedCity() {
      fetch(
        `https://api.openweathermap.org/data/2.5/weather?q=${this.selectedCity}&units=metric&appid=a015a19f3f4cf8e896217cbd4eea6eb6`
      )
        .then((response) => response.json())
        .then((weather) => {
          this.city.temp = weather.main.temp;
          this.city.hum = weather.main.humidity;
          this.city.description = weather.weather[0].description;
        })
        .catch((error) => console.log("error", error));
    },
  },
};
</script>

<style></style>
