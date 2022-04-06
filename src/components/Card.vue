<template>
  <div>
    <div class="col">
      <div
        class="card"
        @mouseover="elementVisible = false"
        @mouseleave="elementVisible = true"
      >
        <img
          v-if="elementVisible"
          :src="'http://image.tmdb.org/t/p/w342/' + cardElement.poster_path"
          class="card-img img-fluid"
          :alt="cardElement.title || cardElement.original_name"
        />
        <div v-else class="card-body">
          <h5 class="card-title">
            <b>Titolo: </b>{{ cardElement.title }} {{ cardElement.name }}
          </h5>
          <p class="card-text">
            <b>Titolo Originale: </b>{{ cardElement.original_title }}
            {{ cardElement.original_name }}
          </p>
          <p class="card-text">
            <b>voto: </b>
            <span
              v-for="n in Math.round(cardElement.vote_average / 2)"
              :key="n"
            >
              <font-awesome-icon icon="fa-solid fa-star" />
            </span>
            <span> {{ cardElement.vote_average }}</span>
          </p>
          <country-flag :country="cardElement.original_language" />
          <div class="card-over">
            <p class="card-info"><b>Overview: </b>{{ cardElement.overview }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "indexCard",
  props: ["cardElement"],
  data: function () {
    return {
      elementVisible: "false",
    };
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
ul {
  border: 1px solid black;
  display: inline-block;
  margin: 0.5rem;
  padding: 1.5rem;
}
.card {
  height: 350px;
  img {
    height: 100%;
  }
  .card-body {
    background-color: black;
    color: white;
    overflow-x: hidden;
    overflow-y: scroll;
  }
  .card-info {
    font-size: 12px;
  }
  b {
    color: rgb(192, 8, 8);
  }
  .fa-star {
    color: gold;
  }
}
</style>
//