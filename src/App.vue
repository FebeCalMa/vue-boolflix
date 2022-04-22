<template>
  <div id="app"></div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",

  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "ead8f8d058a298ee674b1e140e34342f",
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
