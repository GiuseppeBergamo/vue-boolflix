<template>
  <section id="movies">
    <h2>TV Series</h2>
    <BaseCard v-for="serie in series" :key="serie.id" :card="serie"></BaseCard>
  </section>
</template>

<script>
import BaseCard from './BaseCard.vue';
export default {
    name: "SeriesSection",
    props: {
        series: Array,
    },
    components: { BaseCard }
}
</script>

<style>

</style>