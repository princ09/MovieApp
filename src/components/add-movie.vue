<template>
<div id="add-movie" class="container text-center">

    <div class="row">
        <div class="col-md-12">
          <h2>Add a New Movie</h2>
        </div>
    </div>

<div class="row">
        <div class="col-md-6">
          <form>
            <label>Movie Title:</label>
            <input type="text" v-model="movie.Title" required/>
            <label>Add Poster Image Link</label>
            <input type="text" v-model="movie.Link" required/>
            <button id="add-btn" v-on:click.prevent="addToList" class="btn btn-primary">Add Movie</button>
          </form>
        </div>

<div class="col-md-6">
        <div id="preview" >
          <div class="card">
              <div class="poster">
                  <img v-bind:src="movie.Link" alt="">
              </div>
              <div class="details">
                  <h2>{{movie.Title}}</h2>
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
        movie:{
          Title:"",
          Link:""
        },
        userMovie : []
        }


  },
  methods:{
      addToList:function(){
      if(!this.movie) return;
      this.userMovie.push(this.movie);
      console.log(this.userMovie);
      this.saveMovie();
      this.movie.Title="";
      this.movie.Link="";
      },
      saveMovie(){
        let parsed = JSON.stringify(this.userMovie);
        localStorage.setItem('MyMovieList', parsed);
      }
  }
}
</script>

<style scoped>
#add-movie *{
box-sizing : border-box;
}
#add-movie{
  margin:20px auto;
  max-width:500px;
  background:dark-gray;
}
label{
display:block;
margin:20px 0 10px;
}

input[type="text"]{
display:block;
width:100%;
padding:8px;

}

#add-btn{
margin-top:10px;
}
#preview{
padding:10px 20px;
margin:30px 0;
}
h3{
margin-top:10px;
}

.card{
  width: 300px;
  height: 450px;
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
  top:85%;
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
