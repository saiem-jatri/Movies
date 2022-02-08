<template>
<div>
<h2>{{movie.Title}}</h2>
  <p>{{movie.Year}}</p>
  <img :src="movie.Poster" alt="">
  <p>{{movie.Plot}}</p>
</div>
</template>

<script>
import env from "../env.js"
import {ref, onBeforeMount} from 'vue';
import {useRoute} from 'vue-router';
export default {
  setup(){
    const movie= ref({});
    const route=useRoute();
    const loading=ref(false);
    onBeforeMount(()=>{
      console.log(route)
      loading.value=true
      fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&Plot=full`)
      .then(response => response.json())
      .then(data => {
        movie.value=data;
        loading.value=false
        console.log(data)
      });
    })
  return{
      movie
  }
  }

}
</script>

<style scoped>

</style>