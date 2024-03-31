<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="navbar">
    <div>
      <nav>
        <RouterLink to="/">Posts</RouterLink> -
        <!--<RouterLink to="/authors">Authors</RouterLink> -->
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped lang="scss">
.navbar {
  background-color: #9beef1;
  padding: 1.2rem;
}
</style>
