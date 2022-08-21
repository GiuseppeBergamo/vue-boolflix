<template>
    <div class="col">
        <img v-if="!(card.poster_path)" src="../assets/img/No-Image-Placeholder.svg.png" alt="no-image" class="img-fluid rounded h-100">
        <img v-else :src="posterSrc" alt="" id="poster" class="img-fluid rounded h-100">

        <ul class="d-none">
            <li>{{ card.name || card.title}}</li>
            <li>{{ card.original_name || card.original_title }}</li>
            <li>
                <img v-if="card.original_language === 'it' || 'en'" :src="flagImageSrc" :alt="card.original_language" class="w-25">
                <span v-else>{{ card.original_language }}</span>
            </li>
            <li>{{ voteNumber }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'BaseCard',
    props: {
        card: Object,
    },
    computed: {
        flagImageSrc(){
            return require(`../assets/img/${this.card.original_language}.png`);
        },
        posterSrc(){
            return `https://image.tmdb.org/t/p/w342${this.card.poster_path}`;
        }, 
        voteNumber(){
            return Math.ceil((this.card.vote_average) / 2)
        }
    }
}
</script>

<style scoped>

</style>