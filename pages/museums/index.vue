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
      crumbs: [
        {
          withLink: true,
          title: "Home",
          link: "/",
        },
        {
          withLink: false,
          title: "Galerías / Museos",
        },
      ],
    };
  },
  async asyncData({ $content }) {
    const data = await $content("museums")
      .only(["slug", "title", "img", "place"])
      .sortBy("createdAt", "asc")
      .fetch();

    const crumbs = [];

    return {
      data: data.map((e) => ({
        id: e.slug,
        title: e.title,
        img: e.img,
        subTitle: e.place,
        link: { name: "museums-slug", params: { slug: e.slug } },
      }))
    };
  },
};
</script>