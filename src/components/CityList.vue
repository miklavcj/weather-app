<template>
  <v-container id="input-usage">
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
        <v-col cols="6">{{ city }}</v-col>
        <v-col offset="2">
          <v-icon>mdi-white-balance-sunny</v-icon>
          <v-icon @click="removeCity(index)">mdi-close</v-icon>
        </v-col>
      </v-row>
    </div>
  </v-container>
  <!-- <div class="my-6" width="700">
    <AddCity />
    <p v-if="cityList.length === 0">No cities</p>
    <v-card v-else class="mx-auto" max-width="750" tile>
      <v-list>
        <v-subheader>Saved Cities</v-subheader>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-list-item
            v-for="(city, index) in cityList"
            :key="index"
            max-width="750"
            @click="selectedCity = city"
            >{{ city }}

            <v-icon>mdi-white-balance-sunny</v-icon>
            <v-icon @click="removeCity(index)">mdi-close</v-icon></v-list-item
          >
        </v-list-item-group>
      </v-list>
    </v-card>
  </div> -->
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
