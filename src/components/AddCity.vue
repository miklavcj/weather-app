<template>
  <v-container id="input-usage" fluid>
    <v-row>
      <v-col cols="10">
        <v-text-field
          v-model="city"
          label="Add a City"
          id="city"
          filled
        ></v-text-field>
      </v-col>
      <v-col cols="2">
        <v-btn color="primary" outlined small @click="addCity()">Submit</v-btn>
        <v-btn outlined small text @click="city = ''">Cancel</v-btn>
      </v-col>
    </v-row>
  </v-container>
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
    toTitleCase() {
      return this.city
        .toLowerCase()
        .split(" ")
        .map((word) => word.charAt(0).toUpperCase() + word.slice(1))
        .join(" ");
    },
    addCity() {
      if (this.city === "") {
        this.alert = true;
      } else {
        let capitalizedCity = this.toTitleCase();
        this.cityList.push(capitalizedCity);
        this.alert = false;
        this.city = "";

        localStorage.setItem("cityList", JSON.stringify(this.cityList));
      }
    },
  },
};
</script>

<style></style>
