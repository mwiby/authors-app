<script setup>
import { useRoute } from 'vue-router'
import { storeToRefs } from 'pinia'
import { useAuthorStore } from '../stores/author'
import { usePostStore } from '../stores/post'
import Post from '../components/Post.vue'

const route = useRoute()
const { getPostAuthor } = storeToRefs(useAuthorStore())
const { fetchAuthors } = useAuthorStore()
const { fetchPost } = usePostStore()
const { post, loading, error } = storeToRefs(usePostStore())

fetchAuthors()
fetchPost(route.params.id)
</script>

<template>
  <div>
    <p v-if="loading">Loading post...</p>
    <p v-if="error">{{ error.message }}</p>
    <p v-if="post">
      <Post :post="post" :author="getPostAuthor" />
    </p>
  </div>
</template>
