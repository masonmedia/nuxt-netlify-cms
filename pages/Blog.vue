<template>
  <div class="">
    <b-jumbotron
      class="
        d-flex
        flex-column
        justify-content-center
        align-items-start
        mt-3
        mb-2
        mx-4
        shadow
        px-5
        bg-dark
        text-warning
      "
      style="min-height: 300px; border-radius: 33px"
    >
      <h1 class="display-1 font-weight-bold">Blog Posts</h1>
    </b-jumbotron>
    <b-row align-v="center" class="m-3">
      <b-col lg="6" class="p-3" v-for="article of articles" :key="article.slug">
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          <!-- articles list -->
          <b-card
            no-body
            class="bg-dark text-warning overflow-hidden shadow"
            style="border-radius: 33px; min-height: 200px"
          >
            <b-row no-gutters>
              <b-col md="6">
                <b-card-img
                  :src="article.img"
                  class="w-100 h-100 rounded-0"
                  style="object-fit: cover"
                ></b-card-img>
              </b-col>
              <b-col md="6" align-self="center">
                <b-card-body :title="article.title">
                  <b-card-text>
                    {{ article.description }}
                  </b-card-text>
                </b-card-body>
              </b-col>
            </b-row>
          </b-card>
        </NuxtLink>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "Blog",
  async asyncData({ $content, params }) {
    const articles = await $content("articles")
      .only(["title", "description", "img", "slug", "author"])
      .sortBy("createdAt", "asc")
      .fetch();
    return {
      articles,
    };
  },
};
</script>