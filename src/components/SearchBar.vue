<template>
  <div>
    <input type="text" :placeholder="placeholder" v-model="text" @keyup.enter="emitSearch">
    <button type="button" @click="emitSearch"> {{ buttonText }} </button>
  </div>
</template>

<script>
export default {
name: 'SearchBar',
data(){
    return {
        text: '',
    }
},
props: {
    placeholder: String,
    buttonText: String,
},
methods: {
    emitSearch(){
        this.$emit('search', this.text)
    }
}
}
</script>

<style>

</style>