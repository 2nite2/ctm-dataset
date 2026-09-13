<template>
  <div class="p-3 m-3 text-center">
    <p class="mb-2">Simple Bookshelf App by ryuuwiz</p>
    <p class="mb-2">Version {{ version }}</p>
    <a href="https://github.com/ryuuwiz" target="_blank">
      <i class="fab fa-github-alt fa-2x cursor-pointer"></i>
    </a>
  </div>
</template>

<script>
import { version } from '../../package.json'
export default {
  name: 'Footer',
  setup() {
    return {
      version,
    }
  },
}
</script>
