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
          :alt="cardElement.title"
        />
        <div v-else class="card-body">
          <h5 class="card-title"><b>Titolo:</b>{{ cardElement.title }}</h5>
          <p class="card-text">
            <b>Titolo Originale:</b>{{ cardElement.original_title }}
          </p>
          <p
            class="card-text"
            v-if="cardElement.vote_average > 1 && cardElement.vote_average <= 2"
          >
            <b>voto:</b>{{ cardElement.vote_average }}
            <font-awesome-icon icon="fa-solid fa-star" />
          </p>
          <p
            class="card-text"
            v-else-if="
              cardElement.vote_average > 2 && cardElement.vote_average <= 4
            "
          >
            <b>voto:</b>{{ cardElement.vote_average }}
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
          </p>
          <p
            class="card-text"
            v-else-if="
              cardElement.vote_average > 4 && cardElement.vote_average <= 6
            "
          >
            <b>voto:</b>{{ cardElement.vote_average }}
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
          </p>
          <p
            class="card-text"
            v-else-if="
              cardElement.vote_average > 6 && cardElement.vote_average <= 8
            "
          >
            <b>voto:</b>{{ cardElement.vote_average }}
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
          </p>
          <p class="card-text" v-else>
            <b>voto:</b>{{ cardElement.vote_average }}
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
            <font-awesome-icon icon="fa-solid fa-star" />
          </p>
          <country-flag
            :v-if="
              cardElement.original_language === 'en'
                ? 'cardElement.original_language = eh'
                : 'cardElement.original_language'
            "
            :country="cardElement.original_language"
          />
          <div class="card-over">
            <p class="card-info"><b>Overview:</b>{{ cardElement.overview }}</p>
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
  methods: {
    isVisible() {
      this.elementVisible = !this.elementVisible;
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
//