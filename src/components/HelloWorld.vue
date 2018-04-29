<template>
  <div class="hello">
    <input @keyup.enter="search" v-model="query">
    <button @click="search">Search</button>
    <hr>
    <div v-if="movie.Poster !== 'N/A'" v-for="movie in movies" :key="movie.imdbID" class="poster">
      <img :src="movie.Poster" :alt="movie.Title">
      <br>
      <router-link :to="{ name: 'Detail', params: { id: movie.imdbID, name: movie.Title } }">Movie Datail</router-link>
    </div>
  </div>
</template>

<script>
import {mapActions, mapGetters} from 'vuex'

export default {
  name: 'HelloWorld',
  data () {
    return {
      query: 'avenger'
    }
  },
  async created () {
    this.fetchMovies(this.query)
  },
  computed: {
    ...mapGetters(['movies'])
  },
  methods: {
    ...mapActions(['fetchMovies']),
    search () {
      this.fetchMovies(this.query)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.poster {
  display: inline-block;
}
img {
  width: 240px;
}
</style>
