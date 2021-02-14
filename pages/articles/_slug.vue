<template>
  <div>
    <div>
      <h1>{{ article.title }}</h1>
    </div>

    <div class="uk-section">
      <div class="uk-container uk-container-small">
        <!-- eslint-disable vue/no-v-html -->
        <div
          v-if="article.content"
          id="editor"
          v-html="(article.content)"
        />
        <!-- eslint-enable vue/no-v-html
        <p v-if="article.published_at">
          {{ moment(article.published_at).format("MMM Do YY") }}
        </p> -->
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment"

export default {
  async asyncData({ $strapi, params }) {
    const matchingArticles = await $strapi.find("articles", {
      slug: params.slug,
    });
    return {
      article: matchingArticles[0]
    };
  },
  data() {
    return {
      apiUrl: process.env.strapiBaseUri,
    };
  }
}
</script>
