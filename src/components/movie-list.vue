<template>
  <div class="col-md-12">
      <h5 class="text-center">Harry Potter's Movie</h5>
      <div class="container" id="movie">
          <div class="row" id="movies">
          <div v-for="movie in movies" class="col-md-4">
              <div class="card">
                  <div class="poster">
                    <img v-bind:src="movie.Poster" alt="">
                  </div>
                  <div class="details">
                    <h2 v-html="movie.Title"></h2>
                    <a v-on:click="movieSelected(movie.imdbID)"class="btn " href="#">Movie Details></a>
                  </div>
                  </div>
                </div>
          </div>
      </div>
  </div>
</template>

<script>

export default {


  data () {
    return {
      movies:[]

    }
  },
  methods:{
     movieSelected(movieSelected){
     sessionStorage.setItem('movieId', movieSelected);
     this.$emit('hideMovieList', false);
     }
   },
  created() {
   this.axios.get('http://www.omdbapi.com/?apikey=e0620bd4&s=harry potter').then((response) =>{
     this.movies = response.data.Search;
     console.log(this.movies[0].Poster);

   }).catch((err) =>{
     console.log(err);
   });


  }
}
</script>

<style scoped>
.card{
  width: 100%;
  height: 400px;
  background: #000;
  margin-bottom:10px;

}
.card .poster{
  position: relative;
  overflow: hidden;
}
.card .poster:before{
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(0deg , #000 10%, transparent);
}

.card .poster img{
  width: 100%;
}
.details{
  position: absolute;
  padding: 10px;
  width: 100%;
  height: 100%;
  top:70%;
  /*bottom: 0;*/
  left: 0;
  box-sizing: border-box;
  transition: 0.5s;
  z-index: 20;

}
.details h2{
  color: #fff;
  margin: 0;
  padding: 0;
  font-size: 20px;
}

</style>
