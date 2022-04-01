<template>
  <div id="app">
    <Header @search="listTitle" />
    <Main :selectTitle="selectTitle" />
  </div>
</template>

<script>
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
      selectTitle: "",
    };
  },
  methods: {
    listTitle(stringToSearch) {
      this.selectTitle = stringToSearch;
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
