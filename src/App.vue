<template>
  <div id="app">
    <nav>
      <button v-for="toy in toys" :key="toy.id" @click="selectToy(toy.id)">
        {{ toy.name }}
      </button>
    </nav>
    <toys-gallery :favouriteToys="toysFavourite"></toys-gallery>
    <toy-display
      v-if="selectedToyId"
      :fav="toysFavourite.find((toy) => toy.id == this.selectedToyId)"
      :toy="selectedToy"
      @toggle-favourite="toggleToyFavourite"
    ></toy-display>
  </div>
</template>

<script>
import toys from "./assets/toys";
import toyDisplay from "./components/toyDisplay.vue";
import toysGallery from "./components/toysGallery.vue";

export default {
  name: "App",
  components: {
    toyDisplay,
    toysGallery,
  },
  data() {
    return {
      toys,
      selectedToyId: undefined,
      toysFavourite: [],
    };
  },
  computed: {
    selectedToy() {
      return this.toys.find((toy) => toy.id == this.selectedToyId);
    },
  },
  methods: {
    selectToy(toyId) {
      this.selectedToyId = toyId;
    },
    toggleToyFavourite(isToyFav) {
      if (isToyFav) {
        if (!this.toysFavourite.find((toy) => toy.id == this.selectedToyId)) {
          this.toysFavourite.push(this.selectedToy);
        } // findnig an object in an array
      }
      if (!isToyFav) {
        const filteredArray = this.toysFavourite.filter(
          (toy) => toy.id != this.selectedToyId
        );
        this.toysFavourite = filteredArray;
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
