<template>
    <div class="col">
        <div @mouseenter="hover = true" @mouseleave="hover = false" id="posters" class="position-relative text-center h-100">
            <img v-if="!card.poster_path" src="../assets/img/No-Image-Placeholder.svg.png" alt="no-image" class="img-fluid rounded h-100">
            <img v-else :src="posterSrc" alt="" id="poster" class="img-fluid rounded h-100">

            <div id="info" :class="{ 'active' : hover }" class="position-absolute top-0 start-0 h-100 p-5 text-start bg-dark rounded">
                <ul class="text-white p-0 m-0">
                    <li class="mb-3"><span class="me-2"><b>Titolo:</b></span>{{ card.name || card.title}}</li>
                    <li class="mb-3"><span class="me-2"><b>Titolo originale:</b></span>{{ card.original_name || card.original_title }}</li>
                    <li class="mb-3">
                        <span class="me-2"><b>Lingua:</b></span>
                        <img v-if="card.original_language === 'it' || 'en'" :src="flagImageSrc" :alt="card.original_language" class="w-25">
                        <span v-else>{{ card.original_language }}</span>
                    </li>
                    <li class="mb-3"><span class="me-2"><b>Voto:</b></span><i v-for="index in 5" :key="index" :class="voteNumber >= index ? 'fa-solid' : 'fa-regular'" class="fa-regular fa-star"></i></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'BaseCard',
    props: {
        card: Object,
    },
    data() {
        return {
            hover: false
        }
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
    },
    
        
}
</script>

<style scoped>
#info{
    display: none;
    
}

#info.active{
   display: block;
   opacity: 0.50;
   transition: opacity 0.7s ease 0s; 
}


#info.active:hover{
    opacity: 1;
    cursor: pointer;
}

.fa-solid.fa-star{
    color: goldenrod;
}
</style>