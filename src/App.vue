<template>
  <div id="app" class="container">
    <search-form :enabled="isFormEnabled" @search="search" />
    <p class="text-danger" v-show="error">Ha ocurrido un error. Intente de nuevo</p>  
    <repositories-list :repositories="repositories" />
  </div>
</template>

<script>
import SearchForm from './components/SearchForm.vue'
import RepositoriesList from './components/RepositoriesList.vue'

export default {
  name: 'app',
  components: {
    SearchForm,
    RepositoriesList
  },
  data() {
    return {
      searching: false,
      error: false,
      repositories: {
        local: [],
        github: []
      }
    }
  },
  methods: {
    async search(q) {
      this.searching = true
      try {
        const response = await fetch(`http://localhost:8000/search?q=${q}`)
        const repos = await response.json()
        this.repositories = repos
        this.error = false
      }
      catch(err) {
        this.error = true
      }
      this.searching = false
    }
  },
  computed: {
    isFormEnabled() {
      return !this.searching
    }
  }
}
</script>
