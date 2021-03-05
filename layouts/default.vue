<template>
  <div class="app">
    <topbar />
    <Nuxt />
  </div>
</template>

<script>
import Topbar from '@/components/Topbar'

export default {
  components: {
    Topbar,
  },
}
</script>
