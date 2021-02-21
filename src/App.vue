<template>
 <div id='app'>
  <h1>Search</h1>
  <input type='text' v-model='genre' v-on:click='getResult(genre, cast)'>
  <div v-for='result in results' :key='result.id'>
   <p>{{result.title}}</p>
   <img v-bind:src="'http://image.tmdb.org/t/p/w500/' +  result.poster_path" width='200px'>
   </div>
 </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  components: {},
  data() {
    return {
      genre: "",
      results: "",
    };
  },
  methods: {
    getResult(genre, cast) {
      axios
        .get(
          "https://api.themoviedb.org/3/discover/movie?api_key=a4e8485214a389b8af6f13a3549063d5&with_genres=" +
            genre +
            "&with_cast" +
            cast
        )
        .then((response) => {
          this.results = response.data.results;
        });
      console.log(this.results);
    },
  },
};
</script>

<style>
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

