<template>
  <b-container fluid class="p-0">
    <b-jumbotron 
    class="d-flex flex-column justify-content-center align-items-start mb-0 px-5" 
    style="min-height: 500px">
      <h1 class="display-1">{{ article.title }}</h1>
      <p class="h4 font-weight-light">{{ article.description }}</p>
    </b-jumbotron>

    <b-row class="p-5 bg-light" align-v="center">
      <b-col lg="12">
        <!-- <h1>{{ article.title }}</h1>
        <p>{{ article.description }}</p> -->
        <!-- <img style="position: absolute; z-index: 0; top: 0; left: 0" :src="article.img" :alt="article.alt" /> -->
        <p>Post last updated: {{ formatDate(article.updatedAt) }}</p>
        <nuxt-content :document="article" />
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content("articles", params.slug).fetch();

    return { article };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
};
</script>