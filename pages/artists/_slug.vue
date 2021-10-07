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
      article: {},
      crumbs: [
        {
          link: "/",
          title: "Home",
        },
        {
          link: "/artists/",
          title: "Pintores",
        },
      ],
    };
  },
  async asyncData({ $content, params }) {
    const article = await $content("artists", params.slug).fetch();
    const paints = await $content("paints")
      .only(["slug", "title"])
      .where({ artistId: { $eq: article.slug } })
      .fetch();

    const [prev, next] = await $content("artists")
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
      { title: "Nacionalidad", value: article.nationality },
      {
        title: "Nacimiento",
        value: `${article.bornPlace} - ${article.bornDate}`,
      },
      { title: "Muerte", value: article.deathDate },
      createRef('Galería', 'paints-slug', paints)
    ];

    return { article, prev, next };
  },
  created() {
    this.crumbs.push({ title: this.article.title.toUpperCase() });
  },
};
</script>