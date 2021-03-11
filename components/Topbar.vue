<template>
  <div class="topbar">
    <div class="container">
      <a href="/" class="logo">
        <img src="@/assets/images/Rasmus.png" alt="logo-image" />
        <span>@bensoutendijk</span>
      </a>
      <mobile-nav />
      <nav class="topbar-nav">
        <nuxt-link to="/blog" class="topbar-nav-button">Blog</nuxt-link>
        <nuxt-link to="/projects" class="topbar-nav-button">Projects</nuxt-link>
        <nuxt-link to="/about" class="topbar-nav-button">About Me</nuxt-link>
        <div class="topbar-nav-search">
          <i class="fal fa-search"></i>
          <search-input id="topbar-search" />
        </div>
      </nav>
    </div>
  </div>
</template>

<script></script>

<style lang="scss">
@import '~/assets/variables.scss';

.topbar {
  @apply h-20;

  .container {
    @apply flex justify-between items-center;
    @apply h-full w-full mx-auto;

    @media (min-width: 768px) {
      @apply flex-row justify-start;
      max-width: 768px;
    }
  }
  .logo {
    @apply flex items-center;
    @apply mr-2 pl-2 pr-2;

    span {
      @apply ml-2;

      font-family: Quicksand;
    }

    img {
      height: 48px;
    }
  }
}

.topbar-nav {
  @apply hidden;

  @media (min-width: 768px) {
    @apply flex flex-grow;
  }
}

.topbar-nav-button {
  @apply flex justify-center items-center;
  @apply mr-1 ml-1 p-2;
}

.topbar-nav-search {
  @apply flex items-center;
  @apply ml-auto p-2;
  @apply rounded bg-gray-200;

  i {
    @apply mr-1;
  }

  input {
    @apply bg-gray-200;

    &:focus {
      outline: none;
    }
  }

  .search-results {
    @apply h-64 mt-4 p-2;
    @apply bg-white shadow;

    position: absolute;
  }
}
</style>
