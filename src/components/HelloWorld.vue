<template>
  <div class="hello">
    <input @keyup.enter="search" v-model="query">
    <button @click="search">Search</button>
    <hr>
    <div v-if="movie.Poster !== 'N/A'" v-for="movie in movies" :key="movie.imdbID" class="poster">
      <img :src="movie.Poster" :alt="movie.Title">
    </div>
  </div>
</template>

<script>
// import axios from 'axios'
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
    // let movies = await axios.get('http://www.omdbapi.com/?s=avenger&apikey=409a3997')
    // this.movies = movies.data.Search
  },
  computed: {
    ...mapGetters(['movies'])
  },
  methods: {
    ...mapActions(['fetchMovies']),
    search () {
      this.fetchMovies(this.query)
    }
    // async search () {
    //   let movies = await axios.get('http://www.omdbapi.com/?s=' + this.query + '&apikey=409a3997')
    //   this.movies = movies.data.Search
    // }
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
