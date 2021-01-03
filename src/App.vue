<template>
  <v-app>
    <v-main>
      <v-container id="container" class="mt-6">
        <v-row justify="center">
          <AddCity />
        </v-row>
        <v-row justify="center">
          <DisplayCity />
        </v-row>

        <v-row justify="center">
          <CityList />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import CityList from "./components/CityList";
import AddCity from "./components/AddCity";
import DisplayCity from "./components/DisplayCity";

export default {
  name: "App",

  components: {
    CityList,
    AddCity,
    DisplayCity,
  },
};
</script>
<style>
#container {
  border: 1px solid black;
}
</style>
