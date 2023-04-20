<template>
    <div class="relative overflow-hidden bg-white lg:pb-20">
        <div class="pb-80 pt-16 sm:pb-40 sm:pt-24 lg:pb-48 lg:pt-40">
            <div class="relative mx-auto max-w-7xl px-4 sm:static sm:px-6 lg:px-8">
            <div class="sm:max-w-lg">
                <h1 class="font text-4xl font-bold tracking-tight text-gray-900 sm:text-6xl">A web app build with NuxtJS</h1>
                <p class="mt-4 text-xl text-gray-500">This web application was built entirely with NuxtJS as part of my web development training. If you really want to learn more about me, go to my website</p>
            </div>
            <div>
                <div class="mt-10">
                <!-- Decorative image grid -->
                <div aria-hidden="true" class="pointer-events-none lg:absolute lg:inset-y-0 lg:mx-auto lg:w-full lg:max-w-7xl">
                    <div class="absolute transform sm:left-1/2 sm:top-0 sm:translate-x-8 lg:left-1/2 lg:top-1/2 lg:-translate-y-1/2 lg:translate-x-8">
                    <div class="flex items-center space-x-6 lg:space-x-8">
                        <div class="grid flex-shrink-0 grid-cols-1 gap-y-6 lg:gap-y-8">
                        <div class="h-64 w-44 overflow-hidden rounded-lg sm:opacity-0 lg:opacity-100">
                            <img src="https://image.tmdb.org/t/p/original/qNBAXBIQlnOThrVvA6mA2B5ggV6.jpg" alt="" class="h-full w-full object-cover object-center">
                        </div>
                        <div class="h-64 w-44 overflow-hidden rounded-lg">
                            <img src="https://image.tmdb.org/t/p/original/3GrRgt6CiLIUXUtoktcv1g2iwT5.jpg" alt="" class="h-full w-full object-cover object-center">
                        </div>
                        </div>
                        <div class="grid flex-shrink-0 grid-cols-1 gap-y-6 lg:gap-y-8">
                        <div class="h-64 w-44 overflow-hidden rounded-lg">
                            <img src="https://image.tmdb.org/t/p/original/t6HIqrRAclMCA60NsSmeqe9RmNV.jpg" alt="" class="h-full w-full object-cover object-center">
                        </div>
                        <div class="h-64 w-44 overflow-hidden rounded-lg">
                            <img src="https://image.tmdb.org/t/p/original/cvsXj3I9Q2iyyIo95AecSd1tad7.jpg" alt="" class="h-full w-full object-cover object-center">
                        </div>
                        <div class="h-64 w-44 overflow-hidden rounded-lg">
                            <img src="https://image.tmdb.org/t/p/original/s1VzVhXlqsevi8zeCMG9A16nEUf.jpg" alt="" class="h-full w-full object-cover object-center">
                        </div>
                        </div>
                        <div class="grid flex-shrink-0 grid-cols-1 gap-y-6 lg:gap-y-8">
                        <div class="h-64 w-44 overflow-hidden rounded-lg">
                            <img src="https://image.tmdb.org/t/p/original/fnbjcRDYn6YviCcePDnGdyAkYsB.jpg" alt="" class="h-full w-full object-cover object-center">
                        </div>
                        <div class="h-64 w-44 overflow-hidden rounded-lg">
                            <img src="https://image.tmdb.org/t/p/original/6FfCtAuVAW8XJjZ7eWeLibRLWTw.jpg" alt="" class="h-full w-full object-cover object-center">
                        </div>
                        </div>
                    </div>
                    </div>
                </div>

                <NuxtLink to="https://benjamin-benoit.fr" class="inline-block rounded-md border border-transparent bg-green-600 px-8 py-3 text-center font-medium text-white hover:bg-green-700">My website</NuxtLink>
                </div>
            </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
    useHead({
        title: "NuxtFlix | About",
        meta: [
            {
                name: "description", content: "NuxtFlix about page"
            }
        ]
    })
</script>

<style>

</style>