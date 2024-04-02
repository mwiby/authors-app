<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
defineProps(['comments'])
</script>

<template>
  <div class="comment-container">
    <div v-for="comment in comments" :key="comment.id" class="comment">
      <h3 class="comment-name">{{ comment.name }}</h3>
      <p class="comment-body">{{ comment.body }}</p>
    </div>
  </div>
</template>

<style scoped lang="scss">
.comment-container {
  margin-top: 1rem;
}

.comment {
  background-color: #f4f4f4;
  padding: 1rem;
  border-radius: 5px;
  margin-bottom: 1rem;
}

.comment-name {
  margin-bottom: 0.5rem;
  color: #333;
}

.comment-body {
  color: #666;
}
</style>
