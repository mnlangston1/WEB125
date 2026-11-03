<template>
  <div id="app">
    <h1>WEB125 API Demo</h1>
    <button @click="fetchFact">Get Random Fact</button>
    <p v-if="loading">Loading...</p>
    <p v-if="fact">{{ fact }}</p>
    <p v-if="error">{{ error }}</p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data() {
    return { fact: null, loading: false, error: null }
  },
  methods: {
    async fetchFact() {
      this.loading = true
      this.error = null
      try {
        const res = await axios.get('https://uselessfacts.jsph.pl/api/v2/facts/random')
        this.fact = res.data.text
      } catch (e) {
        this.error = 'Failed to load fact.'
      } finally {
        this.loading = false
      }
    }
  }
}
</script>
