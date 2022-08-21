<template>
  <div class="d-flex align-items-center">
    <input type="text" class="form-control" :placeholder="placeholder" v-model="text" @keyup.enter="emitSearch">
    <button type="button" class="btn btn-danger" @click="emitSearch"> {{ buttonText }} </button>
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