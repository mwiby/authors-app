<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
import { RouterLink } from 'vue-router'
import { storeToRefs } from 'pinia'
import { useCommentStore } from '../stores/comment'
import Comment from '../components/Comment.vue'

defineProps(['post', 'author'])

const { getPostComments } = storeToRefs(useCommentStore())
const { fetchComments } = useCommentStore()

fetchComments()
</script>

<template>
  <div class="post-container">
    <h2>{{ post.title }}</h2>
    <p v-if="author" class="post-info">
      Written by:
      <RouterLink :to="`/author/${author.username}`" class="author-link">{{
        author.name
      }}</RouterLink>
      |
      <span class="comments-info">Comments: {{ getPostComments.length }}</span>
    </p>
    <p class="post-body">{{ post.body }}</p>
    <hr class="divider" />
    <h3 class="comments-heading">Comments:</h3>
    <Comment :comments="getPostComments"></Comment>
  </div>
</template>

<style scoped lang="scss">
.post-container {
  padding: 1rem;
  background-color: #f4f4f4;
  border-radius: 5px;
}

.post-info {
  color: #666;
}

.author-link {
  color: #e2b121;
  text-decoration: none;

  &:hover {
    text-decoration: underline;
  }
}

.comments-info {
  margin-left: 1rem;
}

.post-body {
  margin-top: 0.5rem;
  color: #333;
}

.divider {
  margin-top: 1.5rem;
}

.comments-heading {
  margin-top: 1rem;
  color: #333;
}
</style>
