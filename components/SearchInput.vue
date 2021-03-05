<template>
  <div>
    <input v-model="searchQuery" type="text" name="search" autocomplete="off" />
    <ul v-if="posts.length" class="search-results">
      <li v-for="post of posts" :key="post.path">
        <nuxt-link :to="post.path">
          {{ post.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '',
      posts: [],
    }
  },
  watch: {
    async searchQuery(searchQuery) {
      if (!searchQuery) {
        this.posts = []
        return
      }
      this.posts = await this.$content('blog')
        .limit(6)
        .search(searchQuery)
        .fetch()
    },
  },
}
</script>
