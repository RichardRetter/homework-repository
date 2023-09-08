<template>
  <div>
    <h2>Please select an episode from below:</h2>
    <div v-if="isLoading">Loading...</div>
    <div v-else class="movie-list">
      <MovieCards
        v-for="film in films"
        :key="film"
        :film="film"
        @selectedFilm="selectedFilmHandler"
      />
    </div>
  </div>
</template>

<script>
import MovieCards from './MovieCards.vue'
export default {
  data() {
    return {
      isLoading: true,
      films: []
    }
  },
  components: {
    MovieCards
  },
  emits: ['selectedFilm'],
  methods: {
    selectedFilmHandler(film) {
      this.$emit('selectedFilm', film)
    }
  },
  async created() {
    const response = await fetch('https://swapi.dev/api/films')
    const result = await response.json()

    this.films = result.results
    this.isLoading = false
    console.log(this.films)
  }
}
</script>

<style scoped>
.movie-list {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
}
</style>
