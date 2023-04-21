<script setup>

</script>

<template>
    <div v-for="cast in credits.slice(0, 5)">
        <div>
            <div class="card drop-shadow-lg mx-auto bg-gray-900 rounded-lg h-full">
                <img class="rounded" :src="getImageUrl(cast.profile_path)" alt="">
                <p class="text-center font-semibold text-white px-5 py-3">{{ cast.name ?? cast.original_name }}</p>
            </div>
        </div>
    </div>
</template>


<style scoped>

</style>