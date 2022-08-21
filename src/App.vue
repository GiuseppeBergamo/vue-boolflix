<template>
  <div id="app">
    <SearchBar placeholder="Cerca..." buttonText="Cerca" @search="searchData"></SearchBar>

    <MovieSection :movies="movies"></MovieSection>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import axios from 'axios';
import MovieSection from './components/MovieSection.vue';


export default {
  name: 'App',
  components: {
    SearchBar,
    MovieSection
},
  data(){
    return{
      movies: [],
      api: {
        key: "8ad1775a19fb55f243417c7dc5cb78ff",
        baseUri: "https://api.themoviedb.org/3",
        language: "it-IT"
      }
    }
  },
  methods: {
    searchData(query){
      const {key, baseUri, language} = this.api;
      const config = {
        params: {
          api_key: key, 
          language: language,
          query: query,
        }
      }
      axios.get(`${baseUri}/search/movie`, config)
      .then((res) => {
        this.movies = res.data.results;
      })
    }
  }
}
</script>

<style lang="scss">

</style>
