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
          :src="getPoster"
          class="card-img img-fluid"
          :alt="getTitle"
        />
        <div v-else class="card-body">
          <h5 class="card-title">
            <b>Titolo: </b>
            {{ getTitle }}
          </h5>
          <p class="card-text">
            <b>Titolo Originale: </b>
            {{ getOriginal }}
          </p>
          <p class="card-text">
            <b>voto: </b>
            <span v-for="n in getStars" :key="n" class="fa fa-star"> </span>
            <span
              v-for="n in 5 - getStars"
              :key="n + 'star'"
              class="far fa-star"
            >
            </span>
            <span> {{ cardElement.vote_average }}</span>
          </p>
          <country-flag :country="getFlag()" />
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
      isPosted:
        "http://placehold.jp/454867/ffffff/342x350.png?text=Poster%20%0Anot%0Aavailable",
      imgHttp: "http://image.tmdb.org/t/p/w342/",
    };
  },
  methods: {
    getFlag() {
      switch (this.cardElement.original_language) {
        case "en":
          return "gb";
        case "ja":
          return "jp";
        case "zh":
          return "cn";
        default:
          return this.cardElement.original_language;
      }
    },
  },
  computed: {
    getTitle() {
      if (this.cardElement.title) {
        return this.cardElement.title;
      }
      return this.cardElement.name;
    },
    getOriginal() {
      if (this.cardElement.original_title) {
        return this.cardElement.original_title;
      }
      return this.cardElement.original_name;
    },
    getPoster() {
      if (this.cardElement.poster_path == null) {
        return this.isPosted;
      }
      return this.imgHttp + this.cardElement.poster_path;
    },
    getStars() {
      return Math.round(this.cardElement.vote_average / 2);
    },
  },
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