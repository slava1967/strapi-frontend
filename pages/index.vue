<template>
  <div>
    <div class="uk-section">
      <div class="uk-container uk-container-large">
        <Articles :articles="articles" />
      </div>
    </div>
  </div>
</template>

<script>
import Articles from "../components/Articles"

export default {
  components: {
    Articles,
  },
  async asyncData({ $strapi }) {
    return {
      articles: await $strapi.find("articles")
    };
  }
};
</script>
