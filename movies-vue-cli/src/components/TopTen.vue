<template>

    <div class="top-ten-container">
        <div class="top-ten-item" v-for="movie in this.$root.$data.movies" v-bind:key="movie.id">
          <img :src="'/images/'+movie.image">
          <a>{{movie.title}}</a>
        </div>
    </div>

</template>


<script>
export default {
  name: 'TopTen',
  methods: {

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
.top-ten-item a{
    flex:4;
    text-align: center;
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
    font-size: 4.5em;
    margin: 50px 100px;
  }
}
</style>
