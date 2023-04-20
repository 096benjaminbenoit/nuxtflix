<template>
    <main>
        <Hero />
        <h1 class="my-10 text-3xl text-center font-extrabold leading-none tracking-tight text-gray-900 md:text-4xl lg:text-5xl dark:text-black">The most <span class="text-green-600 dark:text-green-500">popular movies</span> of the moment</h1>
        <CardContainer />
    </main>
</template>

<script setup lang="ts">
    useHead({
        title: "NuxtFlix | Home",
        meta: [
            {
                name: "description", content: "NuxtFlix it's a student project to lean Nuxt and Vue"
            }
        ]
    })
</script>

<style>

</style>