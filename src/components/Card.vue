<template>
  <div>
    <ul>
      <li>{{ cardElement.original_title }}</li>
      <li>{{ cardElement.title }}</li>
      <li>{{ cardElement.original_language }}</li>
      <li>{{ cardElement.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "indexCard",
  props: ["cardElement"],
};
</script>

<style lang="scss" scoped>
ul {
  border: 1px solid black;
  display: inline-block;
  margin: 0.5rem;
  padding: 1.5rem;
}
</style>
//