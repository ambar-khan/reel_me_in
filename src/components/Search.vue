<template>
 <div class='search'>
  <h1>Search</h1>
  <input type='text' v-model='query' @keyup='getResult(query)'>
  <div id="container" v-for='result in results' :key='result.id'>
   <p><strong>{{result.title}}</strong></p>
   <p>Release Date: {{result.release_date}}</p>
   <img v-bind:src="'http://image.tmdb.org/t/p/w500/' +    result.poster_path" width='200px'>
   <p>Plot: {{result.overview}}</p>
  </div>
 </div>
</template>
<script>
import axios from "axios";
/*export default {
  name: "search",
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
};*/
</script>