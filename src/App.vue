<template>
  <v-app>
    <v-main>
      <v-container id="container" class="mt-6 blue-grey lighten-5">
        <v-row justify="center">
          <CityList />
        </v-row>
        <v-row justify="center">
          <DisplayCity />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import CityList from "./components/CityList";
import DisplayCity from "./components/DisplayCity";

export default {
  name: "App",

  components: {
    CityList,
    DisplayCity,
  },
};
</script>
<style></style>
