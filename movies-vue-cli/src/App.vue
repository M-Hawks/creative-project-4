<template>
  <div id="app">

    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <router-link class="navbar-brand" to="/">Top 10 Movies</router-link>


      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <router-link class="nav-link" to="/Search">Keyword Search</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/Favorites">Favorites</router-link>
          </li>
        </ul>
      </div>
    </nav>


    <router-view/>


    <footer class="footer">
      <div class="text-center p-3" style="background-color: #383c44;">
        <a class="text-light">Jack Estes and Michael Hawks  |</a>
        <a class="text-light" href="https://github.com/M-Hawks/creative-project-4.git" target="_blank">Github Repository</a>
      </div>
    </footer>

  </div>
</template>

<style>
.footer {
  position: fixed;
  bottom: 0;
  width: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
