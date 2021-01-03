<template>
  <v-container id="input-usage" class="mb-10 bx-auto" width="80%">
    <AddCity />
    <v-subheader>Saved Cities</v-subheader>
    <p v-if="cityList.length === 0">No cities</p>
    <div v-else>
      <v-row
        v-for="(city, index) in cityList"
        :key="index"
        justify="center"
        max-width="750"
        @click="selectedCity = city"
      >
        <v-col cols="6" offset="2">{{ city }}</v-col>
        <v-col offset="2">
          <!-- <v-icon>mdi-white-balance-sunny</v-icon> -->
          <v-icon @click="removeCity(index)">mdi-close</v-icon>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script>
import store from "../assets/store";
import AddCity from "./AddCity";

export default {
  data() {
    return {
      selectedItem: 1,
    };
  },
  components: {
    AddCity,
  },
  computed: {
    apiId() {
      return store.apiId;
    },
    cityList: {
      get() {
        return store.cityList;
      },

      set(newArray) {
        store.cityList = newArray;
      },
    },
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
    removeCity(index) {
      this.cityList.splice(index, 1);
      localStorage.setItem("cityList", JSON.stringify(this.cityList));
    },
  },
  created() {
    if (localStorage.getItem("cityList"))
      this.cityList = JSON.parse(localStorage.getItem("cityList"));
  },
};
</script>

<style></style>
