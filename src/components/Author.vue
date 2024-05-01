<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
import { RouterLink } from 'vue-router'

defineProps(['author', 'posts'])
</script>

<template>
  <div class="container">
    <h1>{{ author.name }}</h1>
    <p>{{ posts.length }} posts written.</p>
    <div class="author-container">
      <div v-for="post in posts" :key="post.id" class="post-card">
        <div class="post">
          <RouterLink :to="`/post/${post.id}`" class="post-link">{{ post.title }}</RouterLink>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  padding: 5px 2px;
}
.author-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
  padding: 0.2rem;
}

.post-card {
  background-color: #f4f4f4;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  margin-top: 1rem;
  padding: 1rem;
}

.post-link {
  color: #000;

  &:hover {
    color: #e2b121;
  }
}
</style>
