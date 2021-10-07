<template>
  <div>
    <breadcrumbs :crumbs="crumbs"></breadcrumbs>
    <div class="container mx-auto flex px-5 md:flex-row flex-col items-center">
      <div
        class="
          lg:flex-grow
          md:w-1/2
          lg:pr-24
          md:pr-16
          flex flex-col
          md:items-start
          md:text-left
          mb-16
          md:mb-0
          items-center
          text-center
        "
      >
        <h1
          class="title-font sm:text-4xl text-3xl mb-4 font-medium text-gray-900"
        >
          Universidad Nacional.<br class="hidden lg:inline-block" />
          Arquitectura de Informacion.<br class="hidden lg:inline-block" />
          Proyecto 1 - Galeria de Arte.<br class="hidden lg:inline-block" />
        </h1>
        <p class="mb-8 leading-relaxed">Nelson Fernandez Luna. 304790982</p>
      </div>
      <div class="lg:max-w-lg lg:w-full md:w-1/2 w-5/6">
        <img
          class="object-cover object-center rounded"
          alt="hero"
          src="https://dummyimage.com/720x600"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      crumbs: [
        {
          withLink: false,
          title: "Home",
        },
      ],
    };
  },
};
</script>