<template>
    <footer class="bg-white shadow dark:bg-gray-900 bottom-0">
        <div class="w-full max-w-screen-xl mx-auto p-4 md:py-8">
            <div class="sm:flex sm:items-center sm:justify-between">
                <NuxtLink to="/" class="flex items-center mb-4 sm:mb-0">
                    <img src="@/assets/nuxtflix-logo.png" class="h-8 mr-3" alt="Flowbite Logo" />
                    <span class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white">NuxtFlix</span>
                </NuxtLink>
                <ul class="flex flex-wrap items-center mb-6 text-sm font-medium text-gray-500 sm:mb-0 dark:text-gray-400">
                    <li>
                        <NuxtLink to="/" class="mr-4 hover:underline md:mr-6 ">Home</NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/about" class="mr-4 hover:underline md:mr-6 ">About</NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/contact" class="mr-4 hover:underline md:mr-6 ">Contact</NuxtLink>
                    </li>
                </ul>
            </div>
            <hr class="my-6 border-gray-200 sm:mx-auto dark:border-gray-700 lg:my-8" />
            <span class="block text-sm text-gray-500 sm:text-center dark:text-gray-400">© 2023 <a href="https://benjamin-benoit.fr/" class="hover:underline">Benjamin Benoit</a></span>
        </div>
    </footer>
</template>