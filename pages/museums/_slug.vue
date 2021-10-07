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
          link: "/museums/",
          title: "Galerías / Museos",
        },
      ],
    };
  },
  async asyncData({ $content, params }) {
    const article = await $content("museums", params.slug).fetch();
    const paints = await $content("paints")
      .only(["slug", "title"])
      .where({ museumId: { $eq: article.slug } })
      .fetch();

    const [prev, next] = await $content("museums")
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
      { title: "País", value: article.country },
      { title: "Estado", value: article.state },
      createRef("Galería", "paints-slug", paints),
    ];

    return { article, prev, next };
  },
  created() {
    this.crumbs.push({ title: this.article.title.toUpperCase() });
  },
};
</script>