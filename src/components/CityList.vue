<template>
  <div>
    <p v-if=" cityList.length === 0">No cities</p>
    <ul v-else>
      <li v-for="(city, index) in cityList" :key="index">
        {{ city }}
      </li>
    </ul>
  </div>
</template>

<script>
import store from "../assets/store";

export default {
  data() {
    return {
      list: [],
      
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
  },
  

};
</script>

<style></style>
