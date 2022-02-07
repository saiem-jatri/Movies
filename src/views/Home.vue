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
  <form @submit.prevent="" class="z-100 mt-5">
    <input type="text" placeholder="what are you looking for">
    <input type="submit" value="Search"/>
  </form>
</template>

<script>

export default {
name:'Home'
}
</script>