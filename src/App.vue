<template>
  <div id="app">
    <Header @search="newSearch" />

    <Main :films="filmsSeries" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data: function () {
    return {
      films: [],
      series: [],
      filmsSeries: [],
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "?api_key=95726d0bcf22976ad19620a973156f8c&query=",
      filmSearch: "",
    };
  },
  created: function () {
    this.newSearch("0");
  },
  methods: {
    newSearch(stringToSearch) {
      this.filmSearch = stringToSearch;
      this.listSeries();
      this.listMovie();
    },

    listMovie() {
      axios
        .get(this.apiUrl + "movie" + this.apiKey + this.filmSearch)
        .then((result) => {
          this.films = result.data.results;
          this.filmsSeries = [...this.films, ...this.series];
          console.table(result.data.results);
        })
        .catch((error) => {
          console.log(this.films);
          console.error(error);
        });
    },
    listSeries() {
      axios
        .get(this.apiUrl + "tv" + this.apiKey + this.filmSearch)
        .then((result) => {
          this.series = result.data.results;
          this.filmsSeries = [...this.films, ...this.series];
          console.log(result.data.results);
        })
        .catch((error) => {
          console.warn(this.series);
          console.error(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/style/style.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
