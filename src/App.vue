<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",

  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
    };
  },
  mounted() {
    const query = "verde";
    const params = {
      query,
      api_key: this.apiKey,
      language: "it-IT",
    };
    axios
      .get(this.apiUrl + "movie", { params })
      .then((response) => {
        console.log(response);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
