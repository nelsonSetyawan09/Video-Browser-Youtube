<template lang="html">
  <div class="search-bar">
      <input type="text" @input="onInput" placeholder="search video">
  </div>
</template>

<script>
    export default {
        name: 'SearchBar',
        methods:{
            onInput(event){
                this.$emit('termChange',event.target.value)
            }
        }
    }
</script>

<style lang="css" scoped="">
    .search-bar input{
        font-size: 18px;
        width: 100%;
        margin-bottom: 10px;
    }
</style>
