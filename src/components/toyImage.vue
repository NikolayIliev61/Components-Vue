<template>
  <img :src="`./assets/img/${url}`" :alt="url" />
</template>

<script>
  export default {
    name: 'toyImage',
    props: {
      url: String
    }
  }
</script>

<style scoped>
  img {
    border-radius: 10%;
    border: 1px solid yellowgreen;
  }
</style>