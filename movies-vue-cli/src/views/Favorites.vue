<template>
  <div class="favorites">
    <div class="favorites-header">
      <h1>Your Favorites<br> Refresh to see changes</h1>

      <p></p>
    </div>

    <FavoritesList :favoriteMovies="orderedFavorites" />
  </div>
</template>

<script>
// @ is an alias to /src
import FavoritesList from '@/components/FavoritesList.vue'
import axios from 'axios';

export default {
  name: 'Favorites',
  components: {
    FavoritesList
  },
  computed: {
    orderedFavorites() {
      return this.items;

      // return this.$root.$data.favorites;
    },
  },
  data() {
    return {
     items: [],
    }
  },
  created() {
    this.getItems();
  },
  methods: {
    async getItems() {
      try {
        let response = await axios.get("/api/items");
        this.items = response.data;
        return true;
      } catch (error) {
        console.log(error);
      }
    },
  }
}
</script>

<style scoped>
.favorites-header {
  display:flex;
  justify-content: center;
  align-items: center;
  margin-top:30px;
  margin-left:30px;
  margin-right:30px;
  margin-bottom:0;
}
</style>
