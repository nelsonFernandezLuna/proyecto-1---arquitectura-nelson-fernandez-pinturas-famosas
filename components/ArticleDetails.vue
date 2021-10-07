<template>
  <div class="mx-auto grid grid-flow-col grid-cols-2 gap-4">
    <div class="w-full lg:pr-10 lg:py-6 mb-6 lg:mb-0 uppercase">
      <h1 class="text-gray-900 text-3xl title-font font-medium">
        {{ article.name }}
      </h1>
      <h2
        v-if="article.date"
        class="text-sm title-font text-gray-500 tracking-widest mb-4"
      >
        {{ article.date }}
      </h2>
      <p class="leading-relaxed mb-4 border-b border-gray-200 pb-2">
        <nuxt-content :document="article" />
      </p>
      <article-sub-details
        v-for="detail in article.details"
        :key="detail.title"
        :detail="detail"
      ></article-sub-details>
    </div>
    <img
      alt="content"
      class="w-full lg:h-auto h-64 object-cover object-center rounded"
      :src="article.img"
    />
  </div>
</template>

<script>
export default {
  props: ["article"],
};
</script>