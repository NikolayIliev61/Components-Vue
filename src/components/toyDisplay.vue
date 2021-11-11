<template>
  <div class="toyDisplay">
    <h2>{{ toy.name }}</h2>
    <toy-image class="toyImage" :url="toy.url"></toy-image>
    <p>{{ toy.description }}</p>
    <label :for="`toydisplay-input-checkbox-${toy.id}`">Favourite</label>
    <input
      :id="`toydisplay-input-checkbox-${toy.id}`"
      type="checkbox"
      v-model="isFav"
      @change="toggleFavourite()"
    />
  </div>
</template>

<script>
import toyImage from "./toyImage.vue";

export default {
  name: "toyDisplay",
  components: {
    toyImage,
  },
  props: {
    toy: Object,
    fav: Object,
  },
  data() {
    return {
      isFav: false,
      //   isFav: this.fav ? true : false,
    };
  },
  watch: {
    fav(valueOfFav) {
      if (valueOfFav) {
        this.isFav = true;
      } else {
        this.isFav = false;
      }
    },
  },
  methods: {
    toggleFavourite() {
      this.$emit("toggle-favourite", this.isFav);
    },
  },
};
</script>

<style scoped>
.toyImage {
  height: 300px;
  max-width: 300px;
}
</style>
