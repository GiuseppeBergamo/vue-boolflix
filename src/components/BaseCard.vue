<template>
    <ul>
        <li>{{ card.name || card.title}}</li>
        <li>{{ card.original_name || card.original_title }}</li>
        <li>
            <img v-if="card.original_language === 'it' || 'en'" :src="flagImageSrc" :alt="card.original_language">
            <span v-else>{{ card.original_language }}</span>
        </li>
        <li>{{ card.vote_average }}</li>
    </ul>
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
        }
    }
}
</script>

<style>

</style>