<template>
  <div class="movie">
    <img class="movieImg" v-bind:src='resultImg'>
    <h2>{{ resultTitle }}</h2>
    <div class="line"></div>
    <div class="description">{{ resultDescription }}</div>
  </div>
</template>

<script>
export default {
  name: 'Movie',
  props: {
    'resultTitle': String,
    'resultImg': String,
    'resultDescription': String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .movie {
    background-color: white;
    border-radius: 20px;
    padding: 20px;
    color: #282828;
    text-align: left;
    width: 340px;
    margin: 20px 10px;
    height: 600px;
    overflow: hidden;
  }
  .movieImg {
    height: 350px;
    width: 300px;
    border-radius: 20px;
    margin-bottom: 10px;
  }
  .movie .line {
    background-color: #d72638;
    height: 10px;
    margin: 10px 0px;
    border-radius: 5px;
    width: 50%;
  }
  .description {
    height: 140px;
    overflow-y: scroll;
  }
</style>
