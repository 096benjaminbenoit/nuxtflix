<template>
    <div v-for="movie in movies.slice(0, 5)">
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
                <span class="hidden absolute top-2 right-2 sm:inline-flex items-center justify-center px-2 py-1 text-xs font-bold leading-none text-red-100 transform translate-x-1/2 -translate-y-1/2 bg-gray-900 rounded-full w-10 h-10 border border-white">{{ movie.vote_average.toFixed(2) }}</span>
            </div>
        </NuxtLink>
    </div>

</template>

<script setup>
    const { data: getPopularMovies } = await useFetch(`https://api.themoviedb.org/3/movie/popular?api_key=6dc5c1a78711cf80c5b1fcc9e7340fb9&language=en-US&page=1
`)
    const movies = toRaw(getPopularMovies.value.results)
        //   console.log(toRaw(movies[0].id))

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