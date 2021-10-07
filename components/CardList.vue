<template>
  <section class="text-gray-600 body-font">
    <div class="container p-5 mx-auto">
      <div class="flex flex-wrap -mx-4 -mb-10 text-center">
        <div class="sm:w-1/2 mb-10 px-4" v-for="ele in data" :key="ele.id">
          <card
            :link="ele.link"
            :img="ele.img"
            :title="ele.title"
            :subTitle="ele.subTitle"
          ></card>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["data"],
};
</script>