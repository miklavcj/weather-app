<template> </template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    getData() {
      fetch(
        `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=a015a19f3f4cf8e896217cbd4eea6eb6`
      )
        .then((response) => response.json())
        .then((result) => {
          console.log(result);
        })
        .catch((error) => console.log("error", error));
    },
  },
};
</script>

<style></style>
