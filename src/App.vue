<template>
 <div id='app'>
  <header>
     <img src="./assets/logo.png" alt="Reel Me In Logo" id="logo">
      <h1>
          Reel Me In
      </h1>
      <div>
          <div id="formpos">
              <div class="group">
                  <label for="genre">Genre</label>
                  </br>
                  <select name="genre" id="genre" v-model='genre'>
                    <option value="null">Don't filter by genre</option>
                    <option value="28">Action</option>
                    <option value="12">Adventure</option>
                    <option value="16">Animation</option>
                    <option value="35">Comedy</option>
                    <option value="80">Crime</option>
                    <option value="99">Documentation</option>
                    <option value="18">Drama</option>
                    <option value="10751">Family</option>
                    <option value="14">Fantasy</option>
                    <option value="36">History</option>
                    <option value="27">Horror</option>
                    <option value="10402">Music</option>
                    <option value="9648">Mystery</option>
                    <option value="10749">Romance</option>
                    <option value="878">Science Fiction</option>
                    <option value="10770">TV Movie</option>
                    <option value="53">Thriller</option>
                    <option value="10752">War</option>
                    <option value="37">Western</option>
                  </select>
              </div>
              <div class="group">
                  <label for="year">Release Year:</label>
                  </br>
                  <input type="number" min="1878" name="year" id="year" v-model='year'>
              </div>
              <div class="group">
                  <label for="min-rating">Minimum Rating: </label>
                  </br>
                  <input type="number" min="0" step="0.1" max="10" name="min-rating" id="min-rating" v-model='minrating'>
              </div>
              <div class="group">
                  <label>Viewing Platform:</label>
                  <br>
                  <select name="providor" id="providor" v-model='providor'>
                    <option value="null">Don't filter by providor</option>
                    <option value="8">Netflix</option>
                    <option value="10">Amazon Video</option>
                    <option value="337">Disney Plus</option>
                  </select>
              </div>
          </div>
          <input type="submit" value="Search" class="button" v-on:click='getResult(genre, year, minrating, providor)'>
      </div>
  </header>
  <div id="movie-container">
    <Movie v-for='result in results' v-bind:resultTitle='result.title' v-bind:resultImg='"http://image.tmdb.org/t/p/w500/" +    result.poster_path' v-bind:resultDescription='result.overview' :key='result.id' />
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
      genre: "",
      year: "",
      minrating: "",
      providor: "",
      results: "",
    };
  },
  methods: {
    getResult(genre, year, minrating, providor) {
      if (year == null) {
        year = "1878";
      }
      if (minrating == null) {
        minrating = "0.0";
      }
      axios
        .get(
          "https://api.themoviedb.org/3/discover/movie?api_key=a4e8485214a389b8af6f13a3549063d5&with_cast=&with_genres=" + genre + "&year=" + year + "&vote_average.gte=" + minrating
        )
        .then((response) => {
          this.results = response.data.results;
        });
        console.log(genre + " " + year + " " + minrating);
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
        background: linear-gradient(0deg, rgba(215,38,56,0) 0%, rgba(215,38,56,1) 100%);
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
        width: 70%;
    }
    .group{
        padding: 10px 50px;
    }
    .button {
        padding: 10px 20px;
        border-radius: 12px;
        border: none;
        background-color: #3F88C5;
        color: #ffffff;
        box-shadow: 1px 1px 0px #ffffff, 2px 2px 0px #f5c9ce, 3px 3px 0px #eb939c, 4px 4px 0px #e15d6a, 5px 5px 0px #d72638;
        transition: all 1s;
        font-size: 1.5rem;
    }
    .button:hover, .button:focus {
        box-shadow: none;
        transform: translate(5px, 5px);
        outline: none;
    }
    #movie-container {
      display: flex;
      justify-content: space-around;
      align-content: center;
      padding: 50px;
      flex-wrap: wrap;
    }
    input[type='number'], select {
      padding: 10px;
      border-radius: 10px;
      outline: none;
      margin: 5px;
    }
</style>

