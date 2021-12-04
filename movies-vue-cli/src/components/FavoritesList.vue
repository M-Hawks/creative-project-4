<template>

    <div class="favorites-list-container">
        <div class="favorites-list-item" v-for="movie in favoriteMovies" v-bind:key="movie.id">
          <img :src="'https://image.tmdb.org/t/p/w500'+movie.poster_path">
          <div class="favorites-list-info">
            <p>Your score: {{movie.score}}/10</p>
            <a class="movie-title">{{movie.title}}</a>
            <p>{{movie.overview}}</p>
            <button v-on:click="deleteItem(movie)">Delete</button>
            <form v-on:submit.prevent="changeScore(movie)">
              <input id="movieInput" type="Number" v-model="newScore">
              <input id="movieSubmit" type="submit" value="Change Score">
            </form>
          </div>
        </div>
    </div>

</template>

<script>
import axios from 'axios';
export default {
  name: 'FavoitesList',
  methods: {
    async deleteItem(item) {
      try {
        await axios.delete("/api/items/" + item._id);
        return true;
      } catch (error) {
        console.log(error);
      }
    },
    async changeScore(item) {
      try {
        await axios.put("/api/items/" + item._id, {
          score: this.newScore,
        });
        this.newScore = null;
        return true;
      } catch (error) {
        console.log(error);
      }
    },

  },
  data() {
    return {
      newScore: Number,

    }
  },
  props: {
    favoriteMovies: Array
  },
}
</script>

<style scoped>
.favorites-list-item {
    display:flex;
    align-items: center;
    justify-content: center;
    font-family: Roboto Condensed,RobotoCondensed-Bold,Roboto,Arial,Helvetica,sans-serif;

    background-color: #dbdbc8;
}

.favorites-list-item img{
    width: 25%;
    flex: 1;
}
.favorites-list-item div{
    flex:4;
    text-align: center;
}


/* Mobile Styles */
@media only screen and (max-width: 450px) {
  .favorites-list-item {
      font-size: 1.2em;
      margin: 30px 40px;
  }
}

/* Tablet Styles */
@media only screen and (min-width: 451px) and (max-width: 960px) {
  .favorites-list-item {
      font-size: 2.5em;
      margin: 30px 75px;
  }
}

/* Desktop Styles */
@media only screen and (min-width: 961px) {
  .favorites-list-item {
    font-size: 1.3em;
    margin: 50px 100px;
  }
  .movie-title {
  font-size: 2em;
  }
}
</style>
