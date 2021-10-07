<template>
  <div>
    <breadcrumbs :crumbs="crumbs"></breadcrumbs>
    <card-list :data="data"></card-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      articles: [],
      crumbs: [
      {
        title: "Home",
        link: "/",
      },
      {
        title: "Galería",
      },
    ]
    }
  },
  async asyncData({ $content }) {
    const data = await $content("paints")
      .only(["slug", "title", "img", "artistName", "createDate"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      data: data.map((e) => ({
        id: e.slug,
        title: e.title,
        img: e.img,
        link: { name: "paints-slug", params: { slug: e.slug } },
      }))
    };
  },
};
</script>