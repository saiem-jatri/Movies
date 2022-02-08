<template>
<div class="Home">
  <router-link to="/movie/hygt">
    <img src="https://m.media-amazon.com/images/M/MV5BZmQ5NGFiNWEtMmMyMC00MDdiLTg4YjktOGY5Yzc2MDUxMTE1XkEyXkFqcGdeQXVyNTA4NzY1MzY@._V1_SX300.jpg" alt="Naruto Poster" class="w-full h-60 relative z-0 object-cover" />
    <div class="absolute text-white left-0 right-0 top-28 z-10 p-4 bg-gray-900 bg-opacity-50">
      <h3 class="text-white mb-4">Naruto</h3>
      <p>Naruto Kazuma, a mischievous adolescent ninja, struggles as he searches for recognition and dreams of becoming the Hokage, the village's leader and strongest ninja.</p>
    </div>
  </router-link>
</div>
  <form @submit.prevent="SearchMovies()" class="z-100 mt- 5 flex items-center flex-col p-4 ">
    <input class="block outline-none border-none appearance-none w-full text-white bg-gray-700 text-sm mb-15 rounded-sm transition-transform p-4" type="text" placeholder="what are you looking for" v-model="search">
    <input class="w-full bg-green-700 p-4 rounded-sm text-white text-lg active:bg-green-900 cursor-pointer" type="submit" :value="processing ? 'loading...' : 'Search' "/>
  </form>
  <div class="flex gap-2">
    <div v-for="movie in movies" :key="movie.imdbID">
          <router-link :to="'/movie/' + movie.imdbID">
            <div class="">
              <img :src="movie.Poster" class="block" alt="Movies Poster"/>
              <div class="">{{movie.Type}}</div>
              <div class="type">{{movie.Year}}</div>
              <div class="type">{{movie.Title}}</div>
            </div>
          </router-link>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import env from '../env.js';
export default {
  setup() {

    const search = ref("");
    const movies = ref([]);
    const processing =ref(false);
    const SearchMovies = () => {
      processing.value=true;
      if (search.value != "") {
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
            .then(response => response.json())
            .then(data => {
              movies.value=data.Search;
              search.value="";
              console.log(movies.value)
              processing.value=false;
            });
      }
    }

    return {
      search,
      movies,
      SearchMovies,
      processing,
    }
  }
}
</script>
<style>
.disables{
  display: none;
}
</style>