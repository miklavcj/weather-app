<template>
  <div>
    <label for="city">Add a City:</label>
    <input v-model="city" placeholder="City" type="text" id="city" />
    <button @click="addCity()">Submit</button>
    <p v-if="alert">Please enter a city</p>
  </div>
</template>

<script>
import store from "../assets/store";

export default {
  data() {
    return {
      city: "",
      alert: false,
    };
  },
  computed: {
    cityList: {
      get() {
        return store.cityList;
      },

      set(newArray) {
        store.cityList = newArray;
      },
    },
  },
  methods: {
    addCity() {
      if (this.city === "") {
        this.alert = true;
      } else {
        this.cityList.push(this.city);
        this.alert = false;
        this.city = "";
      }
    },
  },
};
</script>

<style></style>
