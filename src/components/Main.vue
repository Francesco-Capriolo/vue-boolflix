<template>
  <main class="container-fluid">
    <div
      class="
        row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5
        g-4
        mb-3
      "
    >
      <Card
        v-for="(element, index) in films"
        :key="index"
        :cardElement="element"
      />
    </div>
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
main {
  margin: 0 auto;
  width: 75%;
  overflow: hidden;
}
</style>