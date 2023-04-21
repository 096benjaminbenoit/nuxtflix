<script setup>
    const route = useRoute();
    const { data: getDetails } = await useFetch(`https://api.themoviedb.org/3/movie/${route.params.id}?api_key=6dc5c1a78711cf80c5b1fcc9e7340fb9&language=en-US`)
    const movie = toRaw(getDetails.value)

    const { data: getCredits } = await useFetch(`https://api.themoviedb.org/3/movie/${route.params.id}/credits?api_key=6dc5c1a78711cf80c5b1fcc9e7340fb9&language=en-US`)
    const credits = toRaw(getCredits.value)
    console.log(credits.cast)

    function getImageUrl(path) {
        const baseUrl = 'https://image.tmdb.org/t/p/original';
        return `${baseUrl}${path}`
    }
</script>

<template>
    <div class="relative isolate overflow-hidden bg-white px-6 py-24 sm:py-24 lg:overflow-visible lg:px-0">
        <div class="absolute inset-0 -z-10 overflow-hidden">
            <svg class="absolute left-[max(50%,25rem)] top-0 h-[64rem] w-[128rem] -translate-x-1/2 stroke-gray-200 [mask-image:radial-gradient(64rem_64rem_at_top,white,transparent)]" aria-hidden="true">
            <defs>
                <pattern id="e813992c-7d03-4cc4-a2bd-151760b470a0" width="200" height="200" x="50%" y="-1" patternUnits="userSpaceOnUse">
                <path d="M100 200V.5M.5 .5H200" fill="none" />
                </pattern>
            </defs>
            <svg x="50%" y="-1" class="overflow-visible fill-gray-50">
                <path d="M-100.5 0h201v201h-201Z M699.5 0h201v201h-201Z M499.5 400h201v201h-201Z M-300.5 600h201v201h-201Z" stroke-width="0" />
            </svg>
            <rect width="100%" height="100%" stroke-width="0" fill="url(#e813992c-7d03-4cc4-a2bd-151760b470a0)" />
            </svg>
        </div>
        <div class="mx-auto grid max-w-2xl grid-cols-1 gap-x-8 gap-y-16 lg:mx-0 lg:max-w-none lg:grid-cols-2 lg:items-start lg:gap-y-10">
            <div class="lg:col-span-2 lg:col-start-1 lg:row-start-1 lg:mx-auto lg:grid lg:w-full lg:max-w-7xl lg:grid-cols-2 lg:gap-x-8 lg:px-8">
            <div class="lg:pr-4">
                <div class="lg:max-w-lg">
                    <NuxtLink to="/" class="flex items-center mb-3 hover:underline">
                        <span class="me-3">
                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-left" viewBox="0 0 16 16">
                                <path fill-rule="evenodd" d="M15 8a.5.5 0 0 0-.5-.5H2.707l3.147-3.146a.5.5 0 1 0-.708-.708l-4 4a.5.5 0 0 0 0 .708l4 4a.5.5 0 0 0 .708-.708L2.707 8.5H14.5A.5.5 0 0 0 15 8z"/>
                            </svg>
                        </span>
                        <span>Back to home</span>
                    </NuxtLink>
                <p class="text-base font-semibold leading-7 text-green-600">{{ movie.release_date ?? movie.first_air_date }}</p>
                <h1 class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">{{ movie.title ?? movie.original_name }}</h1>
                <p class="mt-6 text-xl leading-8 text-gray-700">{{ movie.overview }}</p>
                </div>
                <div class="mt-3">
                    <span class="bg-green-100 text-white text-sm font-medium mr-2 px-2.5 py-0.5 rounded dark:bg-green-700" v-for="genre in movie.genres" :key="genre.id">{{ genre.name }}</span>
                </div>
            </div>
        </div>
        <div class="-ml-12 -mt-12 p-12 lg:sticky lg:top-4 lg:col-start-2 lg:row-span-2 lg:row-start-1 lg:overflow-hidden">
            <img class="w-[48rem] max-w-none rounded-xl bg-gray-900 shadow-xl ring-1 ring-gray-400/10 sm:w-[57rem]" :src="getImageUrl(movie.backdrop_path)" alt="">
        </div>
        <div class="lg:col-span-2 lg:col-start-1 lg:row-start-2 lg:mx-auto lg:grid lg:w-full lg:max-w-7xl lg:grid-cols-2 lg:gap-x-8 lg:px-8">
        </div>
    </div>
    <h3 class="mb-5 text-3xl text-center font-extrabold leading-none tracking-tight text-gray-900 md:text-4xl lg:text-5xl dark:text-black">The cast of <span class="text-green-600 dark:text-green-500">"{{ movie.title }}"</span></h3>
    <section class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-5 mx-10 mb-10">
            <div class="card drop-shadow-lg mx-auto bg-gray-900 rounded-lg h-full" v-for="cast in credits.cast.slice(0, 5)">
                <img class="rounded" :src="getImageUrl(cast.profile_path)" alt="">
                    <p class="text-center font-semibold text-white px-5 pt-3">{{ cast.name ?? cast.original_name }}</p>
                    <p class="text-center font-semibold text-white px-5 pb-3">{{ cast.character }}</p>
            </div>
    </section>
    </div>
</template>

<style scoped>

</style>