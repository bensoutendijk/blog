<template>
  <div class="projects-page">
    <div class="container">
      <div class="featured-project">
        <h2>Billboard</h2>
        <p>Kanban boards with no distractions</p>
        <small>
          <span>react redux&nbsp;</span>
          <span><i class="fal fa-heart"></i>&nbsp;mongo db&nbsp;</span>
          <span><i class="fal fa-heart"></i>&nbsp;express js</span>
        </small>
        <div class="features-container">
          <div class="project-feature">
            <h3>Intuitive Drag and Drop</h3>
            <p>Natural movement, Accessibility with keyboard and screen readers.</p>
            <button class="button view-image" aria-label="view full image" @click.prevent="viewImage">
              <img src="~/assets/images/billboard-moving-card.png" alt="Moving cards between two lists." />
            </button>
            <a href="https://billboard.soutendijk.org/sign-up" target="_blank" class="button is-primary">Sign up now</a>
          </div>
          <div class="project-feature">
            <h3>Quick Edit</h3>
            <p>A modern looking UI presents all the most important features front-and-center.</p>
            <button class="button view-image" aria-label="view full image" @click.prevent="viewImage">
              <img src="~/assets/images/billboard-edit-card.png" alt="Moving cards between two lists." />
            </button>
            <a href="https://billboard.soutendijk.org/sign-up" target="_blank" class="button is-primary">Get Started</a>
          </div>
          <div class="project-feature">
            <h3>Move Lists Too!</h3>
            <p>Multiple drag and drop context support allows you to drag and drop lists as well.</p>
            <button class="button view-image" aria-label="view full image" @click.prevent="viewImage">
              <img src="~/assets/images/billboard-moving-list.png" alt="Moving cards between two lists." />
            </button>
            <a href="https://billboard.soutendijk.org/sign-up" target="_blank" class="button is-primary">Get Started</a>
          </div>
        </div>
      </div>
      <div class="projects-container">
        <ul class="projects-list">
          <li class="project-preview"></li>
        </ul>
      </div>
    </div>
    <div v-if="imageView.length" class="modal" @click="closeImage">
      <div class="image-container" @click.stop>
        <img :src="imageView" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imageView: '',
    }
  },
  methods: {
    viewImage(e) {
      this.imageView = e.target.getAttribute('src')
    },
    closeImage() {
      this.imageView = ''
    },
  },
}
</script>

<style lang="scss">
.projects-page {
  .container {
    @apply flex flex-col;
    @apply h-full w-full;
    @apply mx-auto mt-2 p-2;

    @media (min-width: 768px) {
      max-width: 768px;
    }

    .featured-project {
      @apply flex flex-col items-center;

      > h2 {
        @apply text-3xl;
        font-family: Quicksand;
      }

      > p {
        @apply text-lg;
      }

      > small {
        @apply text-center;
      }
    }

    .project-feature {
      @apply flex flex-col items-center justify-center;
      @apply m-2 p-4;
      @apply shadow-lg rounded-xl;

      > * {
        @apply mb-2;
      }
    }

    h2 {
      @apply text-2xl;
      font-family: Quicksand;
    }

    h3 {
      @apply text-xl;
    }

    p {
      @apply text-base;
    }

    .view-image {
      @apply max-w-xs;

      img {
        @apply rounded-xl;
      }
    }
  }

  .modal {
    @apply fixed flex items-center justify-center;
    @apply w-full h-full;

    z-index: 100;
    top: 0;
    right: 0;

    .image-container {
      max-width: 768px;
    }

    &::before {
      @apply absolute;
      @apply w-full h-full;
      @apply bg-gray-600;
      content: '';

      --bg-opacity: 0.5;
      z-index: -1;
      top: 0;
      right: 0;
    }
  }
}
</style>
