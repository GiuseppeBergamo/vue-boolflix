<template>
  <div id="app">
    <SearchBar placeholder="Cerca..." buttonText="Cerca" @search="searchData"></SearchBar>

    <MovieSection :movies="movies"></MovieSection>

    <SeriesSection :series="series"></SeriesSection>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import axios from 'axios';
import MovieSection from './components/MovieSection.vue';
import SeriesSection from './components/SeriesSection.vue'


export default {
  name: 'App',
  components: {
    SearchBar,
    MovieSection,
    SeriesSection
  },
  data(){
    return{
      movies: [],
      series: [],
      api: {
        key: "8ad1775a19fb55f243417c7dc5cb78ff",
        baseUri: "https://api.themoviedb.org/3",
        language: "it-IT"
      }
    }
  },
  methods: {
    searchData(query){

      if(!query){
        this.movies = [];
        this.series = [];
      }

      const {key, language} = this.api;
      const config = {
        params: {
          api_key: key, 
          language: language,
          query: query,
        }
      };
      this.fetchData('/search/movie', config, 'movies');
      this.fetchData('/search/tv', config, 'series');
      
    },
    fetchData(endpoint, config, array){
      axios.get(`${this.api.baseUri}${endpoint}`, config)
      .then((res) => {
        this[array] = res.data.results;
      })
    }
  }
}
</script>

<style lang="scss">

</style>
