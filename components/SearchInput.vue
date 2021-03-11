<template>
  <div class="searchbar">
    <input v-model="searchQuery" type="text" name="search" autocomplete="off" />
    <div v-if="posts.length" class="search-results">
      <ul class="search-results-container">
        <li v-for="post of posts" :key="post.path">
          <nuxt-link :to="post.path">
            {{ post.title }}
          </nuxt-link>
        </li>
      </ul>
    </div>
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
  methods: {
    clear() {
      this.searchQuery = ''
    },
  },
}
</script>
