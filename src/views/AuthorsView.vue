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
  background-color: #f4f4f4;
  padding: 1rem;
  border-radius: 5px;
}

.author-link {
  color: #000;

  &:hover {
    color: #d1ae49;
  }
}
</style>
