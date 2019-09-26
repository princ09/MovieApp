<template>
<div>
<br>
<div class="row">
          <div class="col-md-4">
            <img :src="movieData.Poster" class="img-thumbnail">
          </div>
          <div class="col-md-8">
            <h2>{{movieData.Title}}</h2>
            <ul class="list-group">
              <li class="list-group-item"><strong>Genre:</strong> <span v-html="movieData.Genre"></span></li>
              <li class="list-group-item"><strong>Released:</strong> <span v-html="movieData.Released"></span></li>
              <li class="list-group-item"><strong>Rated:</strong> <span v-html="movieData.Rated"></span></li>
              <li class="list-group-item"><strong>IMDB Rating:</strong> <span v-html="movieData.imdbRating"></span></li>
              <li class="list-group-item"><strong>Director:</strong> <span v-html="movieData.Director"></span></li>
              <li class="list-group-item"><strong>Writer:</strong>  <span v-html="movieData.Writer"></span></li>
              <li class="list-group-item"><strong>Actors:</strong> <span v-html="movieData.Actors"> </span></li>
            </ul>
          </div>
        </div>
        <div class="row">
          <div class="well">
            <h3>Plot</h3>
            <p v-html="movieData.Plot"></p>

            <hr>
            <a v-bind:href="'http://imdb.com/title/'+movieData.imdbID" target="_blank" class="btn btn-primary">View IMDB</a>
            <a href="index.html" class="btn btn-default">Go Back</a>
          </div>
        </div>
        </div>
</template>

<script>

export default {

  data () {
    return {
      movieData: [],


    }
  },
  methods:{

  },

  created() {
  console.log("Runnning");
    let movieId = sessionStorage.getItem('movieId');
     this.axios.get('http://www.omdbapi.com?apikey=e0620bd4&i='+movieId).then((response) =>{
     this.movieData = response.data;
   }).catch((err) =>{
     console.log(err);
   });


  }


}
</script>

<style>

style>
