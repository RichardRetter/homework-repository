<template>
  <div class="movie-card">
    <div>Episode :</div>
    <span>{{ film.episode_id }}</span>
    <div>{{ film.title }}</div>
    <button @click="clickedFilmHandler">SELECT</button>
  </div>
</template>

<script>
export default {
  props: {
    film: {
      type: Object,
      required: false
    }
  },
  emits: ['selectedFilm'],
  methods: {
    clickedFilmHandler() {
      this.$emit('selectedFilm', this.film)
    }
  }
}
</script>

<style scoped>
.movie-card {
  width: 100px;
  min-height: 50px;
  border: 1px solid white;
}
</style>
