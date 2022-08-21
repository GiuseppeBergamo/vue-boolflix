<template>
  <div id="app" class="bg-grey">
    <header class="d-flex justify-content-around align-items-center">
      <div>
        <h1 class="text-danger">BOOLFLIX</h1>
      </div>
      <SearchBar placeholder="Cerca..." buttonText="Cerca" @search="searchData"></SearchBar>
    </header>

    <MovieSection :movies="movies"></MovieSection>

    <SeriesSection :series="series"></SeriesSection>
  </div>
</template>

<script>
import axios from 'axios';
import MovieSection from './components/MovieSection.vue';
import SeriesSection from './components/SeriesSection.vue';
import SearchBar from './components/SearchBar.vue';


export default {
  name: 'App',
  components: {
    MovieSection,
    SeriesSection,
    SearchBar 
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
@import './assets/scss/style.scss';
.bg-grey{
  background-color: gray;
}
#app{
  min-height: 100vh;
}
header {
  height: 80px;
  background-color: black;
}

ul{
  list-style-type: none;
}
</style>
