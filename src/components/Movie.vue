<template>
  <div class="movie">
    <div class="movieImg"></div>
    <h2>Movie Name</h2>
    <div class="line"></div>
    <div>Description description this is a description of the movie that you should definitely watch yes the description of a movie.</div>
  </div>
</template>

<script>
export default {
  name: 'Movie',
  props: {
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
    width: 290px;
    margin: 20px 10px;
  }
  .movieImg {
    background-image: url('https://images.unsplash.com/photo-1559563362-c667ba5f5480?ixid=MXwxMjA3fDB8MHxzZWFyY2h8M3x8cm9zZXxlbnwwfHwwfA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60');
    background-position: center center;
    background-size: 100%;
    height: 250px;
    width: 250px;
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
</style>
