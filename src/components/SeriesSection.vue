<template>
  <section id="series" class="container">
    <h2 class="h1 text-white fw-bold mb-4">TV Series</h2>
    <div class="row row-cols-4 g-3 text-center">
        <BaseCard v-for="serie in series" :key="serie.id" :card="serie"></BaseCard>
    </div>
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

<style scoped>
#series{
    padding-bottom: 200px;
}
</style>