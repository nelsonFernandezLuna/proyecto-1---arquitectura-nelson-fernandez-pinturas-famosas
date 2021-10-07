<template>
  <nuxt-link :to="link">
    <div class="rounded-lg h-64 overflow-hidden">
      <img
        :src="img"
        alt="content"
        class="object-cover object-center h-full w-full"
      />
    </div>
    <h2
      class="title-font text-2xl font-medium text-gray-900 mt-6 mb-3 uppercase"
    >
      {{ title }}
    </h2>
    <p v-if="subTitle" class="leading-relaxed text-base uppercase">
      {{ subTitle }}
    </p>
  </nuxt-link>
</template>

<script>
export default {
  props: ["link", "img", "title", "subTitle"],
};
</script>