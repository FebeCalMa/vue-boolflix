<template>
  <div>
    <h1>Boolflix</h1>
    <input type="text" v-model="query" />
    <button @click="searchEntries">Cerca!</button>
    <h2>films</h2>
    <div v-for="item in films" :key="item.id">
      {{ item.title }}
    </div>
    <h2>Series</h2>
    <div v-for="item in series" :key="item.id">
      {{ item.name }}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HeaderComponent",
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "ead8f8d058a298ee674b1e140e34342f",
      query: "",
      searching: false,
      films: [],
      series: [],
    };
  },

  methods: {
    searchEntries() {
      if (!this.searching && this.query.length > 0) {
        this.queryApi("films").then((response) => {
          this.films = response.data.results;
          this.searching = false;
        });
        this.queryApi("series").then((response) => {
          this.series = response.data.results;
          this.searching = false;
        });
      }
    },
    queryFilmApi() {
      this.queryApi("films");
    },
    querySeriesApi() {
      this.queryApi("series");
    },
    queryApi(searchType) {
      this.searching = true;
      const params = {
        query: this.query,
        api_key: this.apiKey,
        language: "it-IT",
      };
      return axios
        .get(this.apiUrl + searchType, { params })
        .then((response) => {
          console.log(response);
          this.searching = false;
        })
        .catch((error) => {
          console.log(error);
          this.searching = false;
        });
    },
  },
};
</script>

<style></style>
