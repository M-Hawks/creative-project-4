<template>

    <div class="top-ten-container">
        <div class="top-ten-item" v-for="movie in movies" v-bind:key="movie.id">
          <img :src="'https://image.tmdb.org/t/p/w500'+movie.poster_path">
          <div class="movie-info">
            <a class="movie-title">{{movie.title}}</a>
            <p>{{movie.overview}}</p>
            <button v-on:click="addToFavorites(movie)">Add to Favorites</button>
          </div>
        </div>
    </div>

</template>


<script>
import axios from 'axios';

export default {
  name: 'DisplayMovies',
  methods: {
    async addToFavorites(movie) {

          try {
            this.$root.$data.favorites.add(movie);
            await axios.post('/api/items', {
              title: movie.title,
              overview: movie.overview,
              poster_path: movie.poster_path
            });
          } catch (error) {
            console.log(error);
          }

    }

  },
  props: {
    movies: Array
  }
}

</script>


<style scoped>
.top-ten-item {
    display:flex;
    align-items: center;
    justify-content: center;
    font-family: Roboto Condensed,RobotoCondensed-Bold,Roboto,Arial,Helvetica,sans-serif;

    background-color: #dbdbc8;
}

.top-ten-item img{
    width: 25%;
    flex: 1;
}
.top-ten-item div{
    flex:4;
    text-align: center;
}
.movie-info {



}

/* Mobile Styles */
@media only screen and (max-width: 450px) {
  .top-ten-item {
      font-size: 1.2em;
      margin: 30px 40px;
  }
}

/* Tablet Styles */
@media only screen and (min-width: 451px) and (max-width: 960px) {
  .top-ten-item {
      font-size: 2.5em;
      margin: 30px 75px;
  }
}

/* Desktop Styles */
@media only screen and (min-width: 961px) {
  .top-ten-item {
    font-size: 1.3em;
    margin: 50px 100px;
  }
  .movie-title {
  font-size: 2em;
  }
}
</style>
