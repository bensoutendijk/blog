<template>
  <div class="blog-home">
    <div class="container">
      <div v-for="post in posts" :key="post.path">
        <post-preview :post="post" />
      </div>
    </div>
  </div>
</template>

<script>
import PostPreview from '@/components/PostPreview'

export default {
  components: {
    PostPreview,
  },

  async asyncData({ $content }) {
    const posts = await $content('blog').limit(50).only(['title', 'description', 'img', 'tags', 'path']).sortBy('createdAt', 'asc').fetch()

    return { posts }
  },

  head() {
    return {
      title: 'Soutendijk Blog',
    }
  },
}
</script>

<style lang="scss">
.blog-home {
  .container {
    @apply h-full w-full;
    @apply mx-auto mt-2 pl-2;

    @media (min-width: 768px) {
      max-width: 768px;
    }
  }
}
</style>
