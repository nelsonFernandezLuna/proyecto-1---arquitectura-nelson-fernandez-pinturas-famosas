<template>
  <div>
    <breadcrumbs :crumbs="crumbs"></breadcrumbs>
    <article-details :article="article"></article-details>
    <prev-next :prev="prev" :next="next"></prev-next>
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
          link: "/paints/",
          title: "Galería",
        },
      ],
    };
  },
  async asyncData({ $content, params }) {
    const article = await $content("paints", params.slug).fetch();
    const artist = await $content("artists")
      .only(["slug", "title"])
      .where({ slug: { $eq: article.artistId } })
      .fetch();

    const museum = await $content("museums")
      .only(["slug", "title"])
      .where({ slug: { $eq: article.museumId } })
      .fetch();

    const [prev, next] = await $content("paints")
      .only(["slug"])
      .sortBy("createdAt", "asc")
      .surround(params.slug)
      .fetch();

    const createRef = (title, slug, array = []) => ({
      title,
      subDetails: array.map((e) => ({
        id: e.slug,
        label: e.title,
        link: { name: slug, params: { slug: e.slug } },
      })),
    });

    article.details = [
      createRef("Pintor - Autor", "artists-slug", artist),
      createRef("Museo - Galería", "museums-slug", museum),
    ];

    return { article, prev, next };
  },
  created() {
    this.crumbs.push({ title: this.article.title.toUpperCase() });
  },
};
</script>