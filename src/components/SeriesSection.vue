<template>
  <section id="movies">
    <h2>TV Series</h2>
    <ul v-for="serie in series" :key="serie.id">
        <li>{{ serie.name }}</li>
        <li>{{ serie.original_name }}</li>
        <li>{{ serie.original_language }}</li>
        <li>{{ serie.vote_average }}</li>
    </ul>
  </section>
</template>

<script>
export default {
    name: 'SeriesSection', 
    props: {
        series: Array,
    }
}
</script>

<style>

</style>