<template>
  <div>
    <nav-component></nav-component>
    <b-container fluid class="p-0" :style="{'background': article.background }">
      <!-- <b-jumbotron
        class="
          d-flex
          flex-column
          justify-content-center
          align-items-start
          mb-0
          px-5
        "
        style="min-height: 500px"
      >
      <p>Post last updated: {{ formatDate(article.updatedAt) }}</p>
        <h1 class="display-1">{{ article.title }}</h1>
        <p class="h4 font-weight-light">{{ article.description }}</p>
      </b-jumbotron> -->

      <b-row class="p-5" align-v="center">
        <b-col lg="12" class="mt-5">
          <!-- <h1>{{ article.title }}</h1>
        <p>{{ article.description }}</p> -->
          <!-- <img style="position: absolute; z-index: 0; top: 0; left: 0" :src="article.img" :alt="article.alt" /> -->
          <p class="mb-0">Post last updated: {{ formatDate(article.updatedAt) }}</p>
          <h1 class="display-1">{{ article.title }}</h1>
          <p>{{ article.description }}</p> 
          <hr class="bg-secondary">
          <!-- <p class="h4 font-weight-light">{{ article.description }}</p> -->
          <nuxt-content :document="article" />
        </b-col>
      </b-row>
    </b-container>
  </div>
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

<style>
h1,
.nuxt-content h1,
.nuxt-content h2 {
  line-height: 98%;
  margin-bottom: 1.5rem;
}
.nuxt-content p {
  font-size: 21px;
}
</style>