<template>
<div class="col-md-12">
    <h5 class="text-center">My Movie List</h5>
    <div class="container">
        <div class="row" id="movies">
        <div v-for="movie in mymovielist" class="col-md-4">
            <div class="card">
                <div class="poster">
                  <img v-bind:src="movie.Link" alt="">
                </div>
                <div class="details">
                  <h2 v-html="movie.Title"></h2>
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
      mymovielist:[]

    }
  },
  mounted() {

    if(localStorage.getItem('MyMovieList')) {
      try {
        this.mymovielist = JSON.parse(localStorage.getItem('MyMovieList'));
      } catch(e) {
        localStorage.removeItem('MyMovieList');
      }
    }
  },
  methods:{

  },
  created() {
  console.log(this.mymovielist);

  }

}
</script>

<style scoped>
.card{
  width: 100%;
  height: 400px;
  background: #000;

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
