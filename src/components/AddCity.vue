<template>
  <div>
    <v-card elevation="3" class="pa-6 mt-2">
      <v-card-text
        >Add a City:
        <v-text-field v-model="city" label="City" id="city"></v-text-field>
      </v-card-text>

      <v-card-actions>
        <v-btn @click="addCity()">Submit</v-btn>
        <v-btn @click="city = ''">Cancel</v-btn>
      </v-card-actions>
      <v-card-subtitle v-if="alert">Please enter a city</v-card-subtitle>
    </v-card>
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
