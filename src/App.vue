<template>
<div>
  <app-header v-bind:isHidden="isHidden"></app-header>
  <div class="container">

      <div class="row">
      <button class="btn btn-primary" v-on:click.prevent="isHidden = !isHidden">MyList</button>
      <mylist v-if="!isHidden"></mylist>
      </div>
      <div class="row">
      <movie-list v-if="show" v-on:hideMovieList="updateComp($event)"></movie-list>
      </div>

      <div class="row">
      <movie v-if="!show"></movie>
      </div>


  </div>

  <add-movie></add-movie>


</div>
</template>

<script>
import Header from './components/header.vue';
import MovieList from './components/movie-list.vue';
import Movie from './components/movie.vue';
import AddMovie from './components/add-movie.vue';
import MyList from './components/myList.vue';

export default {
  components:{
    'app-header':Header,
    'movie-list':MovieList,
    'movie':Movie,
    'add-movie':AddMovie,
    'mylist' : MyList
  },
  data () {
    return {
      show:true,
      isHidden: true,
      mylist_show:false,
      showList:false
    }
  },
  methods:{
      updateComp:function(value){
      this.show=value;
      }
  }
}
</script>

<style>

style>
