<template>
  <main>
    <Card
      v-for="(element, index) in films"
      :key="index"
      :cardElement="element"
    />
  </main>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "indexMain",
  components: {
    Card,
  },
  props: ["films"],
  data: function () {
    return {
      cardList: [],
    };
  },

  methods: {},
};
</script>

<style lang="scss" scoped>
section {
  margin: 0 auto;
  width: 80%;
  overflow: hidden;
}
</style>