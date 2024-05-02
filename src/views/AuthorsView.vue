<script setup>
import { RouterLink } from 'vue-router'
import { storeToRefs } from 'pinia'
import { useAuthorStore } from '../stores/author'

const { authors } = storeToRefs(useAuthorStore())
const { fetchAuthors } = useAuthorStore()

fetchAuthors()
</script>

<template>
  <div v-if="authors" class="authors-container">
    <div v-for="author in authors" :key="author.id" class="author">
      <RouterLink :to="`/author/${author.username}`" class="author-link">{{
        author.name
      }}</RouterLink>
      <span class="website-link">{{ author.website }}</span>
    </div>
  </div>
</template>
<style scoped lang="scss">
.authors-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
}

.author {
  display: flex;
  flex-direction: column;
  background-color: #f4f4f4;
  padding: 1rem;
  border-radius: 5px;
}

.author-link {
  font-size: 1.1rem;
  font-weight: bold;
  color: #000;
  text-decoration: underline;
  margin-bottom: 0.5rem;

  &:hover {
    color: #d1ae49;
  }
}

.website-link {
  color: #666;
  font-style: italic;
}
</style>
