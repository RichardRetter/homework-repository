<template>
  <div>
    <div v-if="film == undefined">No episode selected</div>
    <div v-else>
      <h2>{{ film.title }}</h2>
      <p>{{ film.opening_crawl }}</p>
      <p>Total characters: {{ characters.length }}</p>
      <ul>
        <li v-for="character in characters" :key="character">{{ character }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      characters: []
    }
  },
  props: {
    film: {
      type: Object,
      required: false
    }
  },
  watch: {
    async film() {
      this.characters = []
      let i = 0
      for (i = 0; i < this.film.characters.length; i++) {
        const charURL = this.film.characters[i]
        const response = await fetch(charURL)
        const result = await response.json()

        this.characters.push(result.name)
        console.log(this.characters)
      }
    }
  }
}
</script>

<style scoped></style>
