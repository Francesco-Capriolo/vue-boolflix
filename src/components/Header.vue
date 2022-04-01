<template>
  <header class="container-fluid">
    <section class="row justify-content-between align-items-center">
      <div class="col-2">
        <img src="../assets/img/netflixlogo.jpg" alt="netflix logo" />
        <span class="text-white">{{ searchTitle }}</span>
      </div>
      <div class="input-group input-group-sm col-5">
        <span class="input-group-text">Search Title</span>
        <input
          type="text"
          class="form-control me-1"
          v-model="searchTitle"
          @keyup.enter="$emit('search', searchTitle)"
        />
        <button class="btn btn-success">click</button>
      </div>
    </section>
  </header>
</template>

<script>
export default {
  name: "indexHeader",
  data: function () {
    return {
      searchTitle: "",
    };
  },
};
</script>

<style scoped lang="scss">
section {
  background-color: #2e3a46;
  height: 8vh;
}
img {
  width: 50px;
}
div .input-group {
  width: 20%;
}
</style>