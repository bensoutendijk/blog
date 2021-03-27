<template>
  <div class="about-page">
    <div class="container">
      <h1 class="article-title">{{ article.title }}</h1>
      <div class="social-links">
        <a v-for="social in article.social" :key="social.href" :href="social.href" target="_blank">
          <i :class="['fab fa-2x', social.icon]"></i>
        </a>
      </div>
      <h3 class="article-description">{{ article.description }}</h3>
      <nuxt-content :document="article" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const article = await $content('about').fetch()

    return { article }
  },
}
</script>

<style lang="scss">
.about-page {
  .container {
    @apply h-full w-full mx-auto;

    @media (min-width: 768px) {
      @apply flex-row justify-start;
      max-width: 768px;
    }
  }

  .social-links {
    @apply w-full;
    @apply flex justify-start;

    a {
      @apply flex justify-center items-center text-center;
      @apply mr-2 h-12 w-24;
      @apply text-black bg-gray-300 rounded;

      @apply duration-75 ease-in;

      font-family: Quicksand;
      font-weight: 700;

      &:hover {
        @apply bg-gray-200;
      }
    }
  }

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

  a {
    @apply text-orange-400;
  }
}
</style>
