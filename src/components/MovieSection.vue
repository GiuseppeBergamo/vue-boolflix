<template>
  <section id="movies">
    <h2>Movies</h2>
    <BaseCard v-for="movie in movies" :key="movie.id" :card="movie"></BaseCard>
  </section>
</template>

<script>
import BaseCard from './BaseCard.vue';
export default {
    name: "MovieSection",
    props: {
        movies: Array,
    },
    components: { BaseCard }
}
</script>

<style>

</style>