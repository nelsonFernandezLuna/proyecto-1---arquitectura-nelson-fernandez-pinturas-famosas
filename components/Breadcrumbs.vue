<template>
  <div
    class="
      container
      mx-auto
      flex flex-wrap
      flex-col
      md:flex-row
      items-center
    "
  >
    <nav
      class="
        md:mr-auto
        md:py-1
        flex flex-wrap
        items-center
        text-base
        justify-center
      "
    >
      <span
        v-for="(crumb, index) in crumbs"
        :key="crumb.id"
        class="mr-2"
        v-bind:class="{
          'md:border-r md:border-gray-400': index !== crumbs.length - 1,
        }"
      >
        <nuxt-link
          v-if="crumb.link"
          :to="crumb.link"
          class="mr-2 hover:text-gray-900"
        >
          {{ crumb.title }}
        </nuxt-link>
        <p v-else class="mr-2hover:text-gray-900">
          {{ crumb.title }}
        </p>
      </span>
    </nav>
  </div>
</template>

<script>
export default {
  props: ["crumbs"],
};
</script>