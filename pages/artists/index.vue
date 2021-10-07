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
          link: "/",
          title: "Home",
        },
        {
          title: "Pintores",
        },
      ],
    };
  },
  async asyncData({ $content }) {
    const data = await $content("artists")
      .only(["slug", "title", "img", "nationality", "bornDate"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      data: data.map((e) => ({
        id: e.slug,
        title: e.title,
        img: e.img,
        subTitle: `${e.nationality} - ${e.bornDate}`,
        link: { name: "artists-slug", params: { slug: e.slug } },
      })),
    };
  },
};
</script>