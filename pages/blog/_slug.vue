<template>
  <article>
    <div class="container">
      <h1 class="article-title">{{ article.title }}</h1>
      <h3 class="article-description">{{ article.description }}</h3>
      <nuxt-content :document="article" />
    </div>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('blog', params.slug).fetch()

    return { article }
  },
  head() {
    return {
      title: this.article.title,
    }
  },
}
</script>

<style lang="scss">
article {
  .article-title {
    margin-bottom: 0;
  }

  .article-description {
    @apply text-base;
  }

  h1 {
    @apply text-4xl;
    @apply mb-4;
    font-family: Quicksand;
  }

  h2 {
    @apply text-3xl;
    @apply mb-4;
    font-family: Quicksand;
  }

  h3 {
    @apply text-2xl;
    @apply mb-4;
    font-family: Quicksand;
  }

  h4 {
    @apply text-xl;
    @apply mb-4;
    font-family: Quicksand;
  }

  p {
    @apply mb-2;
    font-family: OpenSans;
  }

  .container {
    @apply h-full w-2/5 mx-auto;
    @apply pl-2;
  }
}
</style>
