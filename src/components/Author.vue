<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
import { RouterLink } from 'vue-router'

defineProps(['author', 'posts'])
</script>

<template>
  <div class="author-container">
    <h1>{{ author.name }}</h1>
    <p>{{ posts.length }} posts written.</p>
    <div v-for="post in posts" :key="post.id" class="post">
      <RouterLink :to="`/post/${post.id}`" class="post-link">{{ post.title }}</RouterLink>
    </div>
  </div>
</template>

<style scoped lang="scss">
.author-container {
  padding: 1rem;
}

.post {
  margin-top: 1rem;
}

.post-link {
  color: #000;

  &:hover {
    color: #e2b121;
  }
}
</style>
