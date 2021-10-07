<template>
  <footer class="text-gray-600 body-font">      
    <div
      class="container px-5 py-8 mx-auto flex items-center sm:flex-row flex-col"
    >
      <nuxt-link
        :to="prev.slug"
        v-if="prev"
        class="
          flex
          title-font
          font-medium
          items-center
          md:justify-start
          justify-center
          text-gray-900
        "
      >
        <span class="ml-3 text-xl">Previo</span>
      </nuxt-link>
      <p
        class="
          text-sm text-gray-500
          sm:ml-4
          sm:pl-4
          sm:border-l-2 sm:border-gray-200
          sm:py-2
          sm:mt-0
          mt-4
        "
      >
        © 2021 Ing. Nelson Fernandez L.
      </p>
      <nuxt-link
        :to="next.slug"
        v-if="next"
        class="
          inline-flex
          sm:ml-auto
          sm:mt-0
          mt-4
          justify-center
          sm:justify-start
          text-gray-900
        "
      >
        <span class="ml-3 text-xl">Siguiente</span>
      </nuxt-link>
    </div>
  </footer>
</template>

<script>
export default {
  props: {
    prev: {
      type: Object,
      default: () => null,
    },
    next: {
      type: Object,
      default: () => null,
    },
  },
};
</script>