<template>
  <div class="text-sm border-b border-gray-200 py-2">
    <span class="text-gray-500">
      {{ detail.title }}
    </span>

    <span v-if="!detail.subDetails" class="flex justify-end text-gray-400">
      {{ detail.value }}
    </span>

    <span
      v-else
      v-for="subDetail in detail.subDetails"
      :key="subDetail.id"
      class="flex justify-end text-gray-400"
    >
      <nuxt-link
        v-if="subDetail.link"
        :to="subDetail.link"
        class="mr-2 hover:text-gray-900"
      >
        {{ subDetail.label }}
      </nuxt-link>
      <p v-else class="mr-2">
        {{ subDetail.label }}
      </p>
    </span>
  </div>
</template>

<script>
export default {
  props: ["detail"],
};
</script>