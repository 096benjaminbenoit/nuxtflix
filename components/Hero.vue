<template>
    <div class="bg-center bg-no-repeat bg-[url('https://image.tmdb.org/t/p/original//wybmSmviUXxlBmX44gtpow5Y9TB.jpg')] bg-gray-700 bg-blend-multiply">
      <div class="px-4 mx-auto max-w-screen-xl text-center py-24 lg:py-56">
        <h1 class="mb-4 text-4xl font-extrabold tracking-tight leading-none text-white md:text-5xl lg:text-6xl">The best movie place on web</h1>
        <p class="mb-8 text-lg font-normal text-gray-300 lg:text-xl sm:px-16 lg:px-48">Look no further if you're a true movie aficionado. We are the best cinema place on the internet</p>
        <div class="flex flex-col space-y-4 sm:flex-row sm:justify-center sm:space-y-0 sm:space-x-4">
          <div class="w-full">
            <input type="text" v-model="query" @input="searchMovies" class="block w-full p-4 pl-10 text-sm text-gray-900 border border-gray-300 rounded-lg bg-white focus:ring-green-500 focus:border-green-500 dark:bg-gray-800 dark:border-gray-700 dark:placeholder-gray-400 dark:text-white dark:focus:ring-green-500 dark:focus:border-green-500" placeholder="Search your movie here ...">
          </div>
        </div>
      </div>
    </div>
    <div v-if="movies.length > 0">
        <section class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-5 mx-10 mb-10 mt-10">
            <div v-for="movie in movies">
                <NuxtLink v-bind:to="`/details/${movie.id}`">
                    <div class="card drop-shadow-lg mx-auto bg-gray-900 rounded-lg h-full">
                        <img class="rounded" :src="getImageUrl(movie.poster_path)" alt="">
                        <p class="text-center font-semibold text-white px-5 py-3">{{ movie.title ?? movie.original_name }}</p>
                        <div class="overlay rounded bg-gray-900">
                            <div class="text">
                                <h5 class="mb-3 font-bold">{{ movie.title ?? movie.original_name }}</h5>
                                <p class="mb-3">{{ movie.overview }}</p>
                                <p class="mb-3">{{ movie.release_date ?? movie.first_air_date }}</p>
                                <button href="#" type="submit" class="text-white bg-green-700 hover:bg-green-800 focus:ring-4 focus:outline-none focus:ring-green-300 font-medium rounded-lg text-sm px-4 py-2 dark:bg-green-600 dark:hover:bg-green-700 dark:focus:ring-green-800">Details</button>
                            </div>
                        </div>
                        <span class="absolute top-2 right-2 inline-flex items-center justify-center px-2 py-1 text-xs font-bold leading-none text-red-100 transform translate-x-1/2 -translate-y-1/2 bg-gray-900 rounded-full w-10 h-10 border border-white">{{ movie.vote_average.toFixed(2) }}</span>
                    </div>
                </NuxtLink>
            </div>
        </section>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const query = ref('')
  const movies = ref([])
  
  const searchMovies = async () => {
    if (query.value.length < 3) {
      movies.value = []
      return
    }
  
    const apiKey = '6dc5c1a78711cf80c5b1fcc9e7340fb9'
    const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&query=${query.value}`)
    const data = await response.json()
  
    movies.value = data.results
  }

  function getImageUrl(path) {
        const baseUrl = 'https://image.tmdb.org/t/p/original';
        return `${baseUrl}${path}`
    }
  </script>

<style scoped>
.card {
    transition: 0.4s;
}
.card:hover {
    scale: 1.02;
}

.overlay {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100%;
  width: 100%;
  opacity: 0;
  transition: .5s ease;
}

.card:hover .overlay {
  opacity: 0.9;
}

.text {
  color: white;
  font-size: 14px;
  position: absolute;
  width: 90%;
  height: 90%;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}
</style>
  