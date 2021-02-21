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
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <h1>Search</h1>
  <input type='text' v-model='query' @keyup='getResult(query)'>
  <div v-for='result in results' :key='result.id'>
   <p>{{result.title}}</p>
   <img v-bind:src="'http://image.tmdb.org/t/p/w500/' +    result.poster_path" width='100px'>
   </div>
 </div>
</template>
<script>
import axios from "axios";
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld
  },
  data() {
    return {
      query: "",
      results: "",
    };
  },
  methods: {
    getResult(query) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=a4e8485214a389b8af6f13a3549063d5&query=" +
            query
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
  color: #ffffff;
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
    header {
        background: linear-gradient(0deg, rgba(215,38,56,0) 0%, rgba(215,38,56,1) 100%);
        padding-bottom: 50px;
    }
    #logo {
        max-width: 100%;
        width: 100px;
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
    .group{
        padding: 10px 50px;
    }
    .button {
        padding: 7px 14px;
        border-radius: 12px;
        border: none;
        background-color: #3F88C5;
        color: #ffffff;
        box-shadow: 1px 1px 0px #ffffff, 2px 2px 0px #f5c9ce, 3px 3px 0px #eb939c, 4px 4px 0px #e15d6a, 5px 5px 0px #d72638;
        transition: all 1s;
    }
    .button:hover, .button:focus {
        box-shadow: none;
        transform: translate(5px, 5px);
        outline: none;
    }
</style>
