<template>
  <div class="pa-6">
    <p v-if="cityList.length === 0">No cities</p>
    <v-card v-else class="mx-auto" max-width="300" tile>
      <v-list>
        <v-subheader>Saved Cities</v-subheader>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-list-item
            v-for="(city, index) in cityList"
            :key="index"
            @click="selectedCity = city"
            >{{ city }}</v-list-item
          >
        </v-list-item-group>
      </v-list>
    </v-card>
  </div>
</template>

<script>
import store from "../assets/store";

export default {
  data() {
    return {
      selectedItem: 1,
    };
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
};
</script>

<style></style>
