<template>
  <div id="app">
   
    <AddCity />

    <CityList />
  </div>
</template>
<script>
// @ is an alias to /src
import CityList from "@/components/CityList.vue";
import AddCity from "@/components/AddCity.vue";

export default {
  name: "Home",
  components: {
    CityList,
    AddCity
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
