<template>
  <div class="">
    <nav-component></nav-component>
    <b-container fluid class="mt-5">
      <b-row class="pt-5">
        <b-col
          lg="8"
          class="
            d-flex
            flex-column
            justify-content-center
            align-items-center
            text-center
            mx-auto
            w-100
            p-5
          "
        >
          <h1 class="display-2">Posts</h1>
          <p class="text-secondary font-weight-light h4">
            Minim aliquip id ullamco fugiat enim. Proident laborum ut et nisi
            anim do ea. Incididunt ut in officia Lorem ut occaecat nisi elit
            dolore dolore.
          </p>
        </b-col>
      </b-row>
      <b-row align-v="center" class="my-3">
        <b-col
          lg="6"
          class="p-3"
          v-for="article of articles"
          :key="article.slug"
        >
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
    </b-container>
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