<template>
  <div>
    <ul>
      <li>{{ cardElement.original_title }}</li>
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
</style>
//