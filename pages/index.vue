<template>
  <div class="container">
    <div v-if="error">
      {{ error }}
    </div>
    <ul v-else>
      <li v-for="category in categories" :key="category.id">
        {{ category.name }}
      </li>
    </ul>
    <Nuxt />
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      categories: [],
      error: null,
    }
  },
  async mounted() {
    try {
      const response = await this.$axios.get('/categories')
      this.categories = response.data
    } catch (error) {
      this.error = error
    }
  },
}
</script>
