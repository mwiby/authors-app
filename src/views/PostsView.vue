<script setup>
import { RouterLink } from 'vue-router'
import { storeToRefs } from 'pinia'
import { usePostStore } from '../stores/post'

const { posts, loading, error } = storeToRefs(usePostStore())
const { fetchPosts } = usePostStore()

fetchPosts()
</script>

<template>
  <main>
    <p v-if="loading">Loading posts...</p>
    <p v-if="error">{{ error.message }}</p>
    <div v-if="posts" class="posts-container">
      <div v-for="post in posts" :key="post.id" class="post">
        <RouterLink :to="`/post/${post.id}`" class="post-title">{{ post.title }}</RouterLink>
        <p class="post-body">{{ post.body }}</p>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
.main {
  padding: 1rem;
}

.posts-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1rem;
}

.post {
  background-color: #f4f4f4;
  padding: 1rem;
  border-radius: 5px;
}

.post-title {
  font-size: 1.2rem;
  color: #333;

  &:hover {
    color: #d1ae49;
  }
}

.post-body {
  margin-top: 0.5rem;
  color: #666;
}
</style>
