<template>
  <main>
    <Card
      v-for="(element, index) in cardList"
      :key="index"
      :cardElement="element"
    />
    <p>{{ selectTitle }}</p>
  </main>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";

export default {
  name: "indexMain",
  components: {
    Card,
  },
  props: ["selectTitle"],
  data: function () {
    return {
      cardList: [],
      genresList: [],
    };
  },
  created: function () {
    this.getApi();
  },
  methods: {
    getApi() {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=95726d0bcf22976ad19620a973156f8c&query=" +
            `${this.selctTitle}`
        )
        .then((result) => {
          this.cardList = result.data.results;
          console.table(
            "https://api.themoviedb.org/3/search/movie?api_key=95726d0bcf22976ad19620a973156f8c&query=" +
              `${this.selctTitle}`
          );
          this.$emit("loadMovie", this.genresList);
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
section {
  margin: 0 auto;
  width: 80%;
  overflow: hidden;
}
</style>