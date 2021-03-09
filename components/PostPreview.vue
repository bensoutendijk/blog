<template>
  <nuxt-link :to="post.path">
    <div class="post-preview">
      <img :src="require(`~/assets/images/${post.img}`)" />
      <div class="post-preview-content">
        <h2 class="post-title">{{ post.title }}</h2>
        <p class="post-description">{{ post.description }}</p>
        <div class="post-tags">
          <div v-for="tag in tags" :key="tag" class="chip">{{ tag }}</div>
        </div>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  computed: {
    tags() {
      return this.post.tags.split(',').map((tag) => tag.trim())
    },
  },
}
</script>

<style lang="scss">
.post-preview {
  @apply flex flex-col;
  @apply p-4 rounded;

  @media (min-width: 768px) {
    @apply flex-row;
  }

  h2 {
    @apply text-xl;

    font-family: Quicksand;
  }

  p {
    @apply text-base;

    font-family: OpenSans;
  }

  &:hover {
    @apply bg-gray-200;
  }

  img {
    @apply h-24 w-full;

    @media (min-width: 768px) {
      @apply w-24;
    }
  }
}

.post-preview-content {
  @apply p-2;
  @apply flex flex-col;

  .post-description {
    @apply flex-grow;
  }
}

.post-tags {
  @apply flex flex-wrap;
}
</style>
