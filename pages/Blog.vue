<template>
  <div class="">
    <nav-component></nav-component>
    <b-container fluid class="mt-5">
      <b-row class="pt-5">
        <b-col
          lg="7"
          class="
            d-flex
            flex-column
            justify-content-center
            align-items-start
            w-100
            p-5
          "
        >
        <h4>{{ formatDate(article.date )}}</h4>
          <h1 class="display-1 font-weight-bold lh-sm"><span class="text-primary">Random</span> posts about <span class="text-danger">random</span> things.</h1>
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
              class="bg-light text-secondary overflow-hidden shadow"
              style="border-radius: 33px; min-height: 200px"
            >
              <b-row no-gutters>
                <b-col md="6" class="p-3">
                  <b-card-img
                    :src="article.img"
                    class="w-100 h-100 shadow"
                    style="object-fit: cover; border-radius: 33px"
                  ></b-card-img>
                </b-col>
                <b-col md="6" align-self="center" class="p-3 p-md-0">
                  <b-card-body>
                    <p class="font-weight-light mb-2">{{ formatDate(article.date) }}</p>
                    <h3>{{ article.title }}</h3>
                    <b-card-text>
                      {{ article.description }}
                    </b-card-text>
                    <div class="btn btn-outline-primary">Read more</div>
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
      .only(["title", "description", "img", "slug", "date", "author"])
      .sortBy("createdAt", "asc")
      .fetch();
    return {
      articles,
    };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  }
};
</script>