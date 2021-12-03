<template>
  <div class="home">
    <div class="home-header">
      <h1>Our Top 10 Movies</h1>
    </div>

    <TopTen/>
  </div>
</template>

<script>
// @ is an alias to /src
import TopTen from '@/components/TopTen.vue'

export default {
  name: 'Home',
  components: {
    TopTen
  }
}
</script>

<style scoped>
.home-header {
  display:flex;
  justify-content: center;
  align-items: center;
  margin-top:30px;
  margin-left:30px;
  margin-right:30px;
  margin-bottom:0;
}
</style>
