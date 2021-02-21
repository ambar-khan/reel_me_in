<template>
 <div id='app'>
  <header>
     <img src="./assets/logo.png" alt="Reel Me In Logo" id="logo">
      <h1>
          Reel Me In
      </h1>
      <form>
          <div id="formpos">
              <div class="group">
                  <p>
                      heheh
                  </p>
                  <p>
                      yeet
                  </p>
              </div>
              <div class="group">
                  <p>
                      heheh
                  </p>
                  <p>
                      yeet
                  </p>
              </div>
              <div class="group">
                  <p>
                      heheh
                  </p>
                  <p>
                      yeet
                  </p>
              </div>
              <div class="group">
                  <p>
                      heheh
                  </p>
                  <p>
                      yeet
                  </p>
              </div>
          </div>
          <input type="submit" value="Search" class="button">
      </form>
  </header>
  <div id="movie-container">
    <Movie />
  </div>
  <h1>Search</h1>
  <input type='text' v-model='query'>
  <input type='text' v-model='query2'>
  <button v-on:click='getResult(query, query2)'>Search</button>
  <div v-for='result in results' :key='result.id'>
   <p>{{result.title}}</p>
   <img v-bind:src="'http://image.tmdb.org/t/p/w500/' +    result.poster_path" width='100px'>
   </div>
 </div>
</template>
<script>
import axios from "axios";
import Movie from "./components/Movie";

export default {
  name: "App",
  components: {
    Movie
  },
  data() {
    return {
      query: "",
      query2: "",
      results: "",
    };
  },
  methods: {
    getResult(query, query2) {
      console.log("m");
      axios
        .get(
          "https://api.themoviedb.org/3/discover/movie?api_key=a4e8485214a389b8af6f13a3549063d5&with_cast=" +
            query +
            "&with_genres=" +
            query2
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
  text-align: center;
  color: #ffffff;
}
header {
  background: linear-gradient(
    0deg,
    rgba(215, 38, 56, 0) 0%,
    rgba(215, 38, 56, 1) 100%
  );
  padding-bottom: 50px;
}
#logo {
  max-width: 100%;
  width: 300px;
  margin: 18px auto;
}
#formpos {
  margin: auto;
  padding: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  width: 50%;
}
.group {
  padding: 10px 50px;
}
.button {
  padding: 7px 14px;
  border-radius: 12px;
  border: none;
  background-color: #3f88c5;
  color: #ffffff;
  box-shadow: 1px 1px 0px #ffffff, 2px 2px 0px #f5c9ce, 3px 3px 0px #eb939c,
    4px 4px 0px #e15d6a, 5px 5px 0px #d72638;
  transition: all 1s;
}
.button:hover,
.button:focus {
  box-shadow: none;
  transform: translate(5px, 5px);
  outline: none;
}
#movie-container {
  display: flex;
  justify-content: space-around;
  align-content: flex-start;
  padding: 50px;
  flex-wrap: wrap;
}
</style>

