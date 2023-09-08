<template>
  <div class="main-parts">
    <div>
      <MovieListVue @selectedFilm="selectedFilmHandler" />
    </div>
    <div>
      <MovieDetails :film="selectedFilm" />
    </div>
  </div>
</template>

<script>
import MovieDetails from './components/MovieDetails.vue'
import MovieListVue from './components/MovieList.vue'
export default {
  data() {
    return {
      selectedFilm: undefined
    }
  },
  methods: {
    selectedFilmHandler(film) {
      this.selectedFilm = film
    }
  },
  components: {
    MovieListVue,
    MovieDetails
  }
}
</script>

<style scoped>
.main-parts {
  display: flex;
  gap: 20px;
  margin: 0 auto;
  width: 820px;
}
.main-parts > div {
  width: 400px;
  min-height: 600px;
  border: 3px solid white;
}
</style>
