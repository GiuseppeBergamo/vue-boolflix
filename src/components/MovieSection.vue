<template>
  <section id="movies" class="container">
    <h2 class="h1 text-white fw-bold mb-4">Movies</h2>
    <div class="row row-cols-4 g-3 text-center">
        <BaseCard v-for="movie in movies" :key="movie.id" :card="movie"></BaseCard>
    </div>
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

<style scoped>
#movies{
    margin-top: 300px;
    margin-bottom: 100px;
}
</style>