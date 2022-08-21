<template>
  <section id="movies">
    <h2>Movies</h2>
    <ul v-for="movie in movies" :key="movie.id">
        <li>{{ movie.title }}</li>
        <li>{{ movie.original_title }}</li>
        <li>{{ movie.original_language }}</li>
        <li>{{ movie.vote_average }}</li>
    </ul>
  </section>
</template>

<script>
export default {
    name: 'MovieSection', 
    props: {
        movies: Array,
    }
}
</script>

<style>

</style>