<template>
    <div class="toysGallery">
        <toy-image class="toyImageThumbnail" v-for="toy in favouriteToys" :key="toy.id" :url="toy.url"></toy-image>
    </div>
</template>

<script>
import toyImage from './toyImage.vue'

export default {
    name: 'toysGallery',
    components: {
        toyImage
    },
    props: {
        favouriteToys: Array
    }
}
</script>

<style scoped>
.toyImageThumbnail{
    height: 60px;
    max-width: 60px;
}
</style>