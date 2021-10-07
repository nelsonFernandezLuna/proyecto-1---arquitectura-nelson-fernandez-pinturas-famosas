<template>
  <header class="text-gray-600 body-font">
    <div class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center">
      <nuxt-link to="/" class="flex title-font font-medium items-center text-gray-900 mb-4 md:mb-0">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" class="w-10 h-10 text-white p-2 bg-indigo-500 rounded-full" viewBox="0 0 24 24">
          <path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"></path>
        </svg>
        <span class="ml-3 text-xl">Galería</span>
      </nuxt-link>
      <nav class="md:mr-auto md:ml-4 md:py-1 md:pl-4 md:border-l md:border-gray-400	flex flex-wrap items-center text-base justify-center">
        <nuxt-link to="/paints" class="mr-5 hover:text-gray-900">Galería</nuxt-link>
        <nuxt-link to="/artists" class="mr-5 hover:text-gray-900">Pintores</nuxt-link>
        <nuxt-link to="/museums" class="mr-5 hover:text-gray-900">Galerías / Museos</nuxt-link>
        <nuxt-link to="/search" class="mr-5 hover:text-gray-900">Búsqueda</nuxt-link>
      </nav>
    </div>
  </header>
</template>

<style>
a.nuxt-link-active {
  font-weight: bold;
}
</style>
