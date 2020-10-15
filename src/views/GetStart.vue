<template>
  <article class="markdown-body" v-html="md">
  </article>
</template>

<script lang="ts">
import md from '../mardown/get-started.md';

export default {
  data() {
    return {
      md
    }
  }
}
</script>