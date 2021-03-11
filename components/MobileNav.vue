<template>
  <div class="mobile-nav">
    <button class="button mr-2" @click="toggle">
      <i class="fal fa-bars"></i>
    </button>
    <div :class="['content', { 'is-active': isActive }]">
      <div class="bar">
        <div class="container">
          <div class="search">
            <i class="fal fa-search"></i>
            <search-input id="mobile-search" ref="search" />
          </div>
          <button class="close button" @click="toggle">
            <i class="fal fa-times"></i>
          </button>
        </div>
      </div>

      <nav @click="toggle">
        <nuxt-link to="/blog" class="button">
          <span>Blog</span>
        </nuxt-link>
        <nuxt-link to="/projects" class="button">
          <span>Portfolio</span>
        </nuxt-link>
        <nuxt-link to="/about" class="button">
          <span>About Me</span>
        </nuxt-link>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isActive: false,
    }
  },
  watch: {
    $route() {
      if (this.isActive) {
        this.toggle()
      }
    },
  },
  methods: {
    toggle() {
      this.isActive = !this.isActive

      this.$refs.search.clear()
    },
  },
}
</script>

<style lang="scss">
.mobile-nav {
  .bar {
    @apply h-20;
    @apply flex;
  }

  .content {
    @apply fixed;
    @apply bg-white w-0 h-full;

    @apply duration-75 ease-out;

    z-index: 1;
    top: 0;
    right: 0;
    overflow-x: hidden;
  }

  nav {
    @apply flex flex-col;
  }

  .search {
    @apply flex flex-grow items-center;
    @apply m-2;

    .searchbar {
      @apply w-full;
    }

    .search-results {
      @apply fixed w-full h-full mt-16;

      top: 0;
      left: 0;

      overflow-x: hidden;
    }

    .search-results-container {
      @apply h-full w-full flex flex-col items-center pt-4;
      @apply bg-white rounded;
    }

    input {
      @apply h-10 w-full ml-2 pl-2;
      @apply rounded bg-gray-300;
    }
  }

  .is-active {
    @apply w-full;
  }

  .close {
    @apply m-2;
    float: right;
  }

  @media (min-width: 768px) {
    @apply hidden;
  }
}
</style>
