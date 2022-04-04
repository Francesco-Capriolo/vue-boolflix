<template>
  <div id="app">
    <Header @search="listTitle" />
    <Main :films="films" />
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
      films: "",
    };
  },
  created: function () {},
  methods: {
    listTitle(stringToSearch) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=95726d0bcf22976ad19620a973156f8c&query=${stringToSearch}`
        )
        .then((result) => {
          this.films = result.data.results;
          console.log(result.data);
        })
        .catch((error) => {
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
  text-align: center;
  color: #2c3e50;
}
</style>
