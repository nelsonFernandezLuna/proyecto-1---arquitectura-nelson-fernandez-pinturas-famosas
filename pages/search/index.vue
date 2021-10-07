<template>
  <div>
    <breadcrumbs :crumbs="crumbs"></breadcrumbs>
    <div
      class="container mx-auto flex flex-wrap flex-col md:flex-row items-center"
    >
      <div class="relative sm:w-64 w-40 sm:mr-4 mr-2">
        <label for="footer-field" class="leading-7 text-sm text-gray-600"
          >Buscar</label
        >
        <input
          type="text"
          id="footer-field"
          name="footer-field"
          v-model="searchQuery"
          class="
            w-full
            bg-gray-100 bg-opacity-50
            rounded
            border border-gray-300
            focus:ring-2
            focus:bg-transparent
            focus:ring-indigo-200
            focus:border-indigo-500
            text-base
            outline-none
            text-gray-700
            py-1
            px-3
            leading-8
            transition-colors
            duration-200
            ease-in-out
          "
        />
      </div>
    </div>
    <card-list :data="articles"></card-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
      articles: [],
      crumbs: [
        { 
          link: "/",
          title: "Home",
        },
        { title: "Busqueda" },
      ],
    };
  },
  watch: {
    async searchQuery(searchQuery) {
      if (!searchQuery) {
        this.articles = [];
        return;
      }

      console.log(searchQuery)

      const data = await this.$content("/", { deep: true })
        .only(["slug", "title", "img", "path"])
        .search('name', searchQuery)
        .fetch();

      console.log(data);
      this.articles = data.map((e) => ({
        id: e.slug,
        title: e.title,
        img: e.img,
        subTitle: "",
        link: e.path,
      }));
    },
  },
};
</script>