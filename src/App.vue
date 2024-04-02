<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="navbar">
    <div>
      <nav>
        <RouterLink to="/">Posts</RouterLink>
        <span class="separator">|</span>
        <RouterLink to="/authors">Authors</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped lang="scss">
.navbar {
  background-color: #486363;
  padding: 1.2rem;
  margin-bottom: 0.8rem;
}

nav {
  display: flex;
  align-items: center;
}

nav a {
  color: #fff;
  text-decoration: none;
  padding: 0.2rem;

  &:hover {
    color: #ffd166;
  }
}

.separator {
  color: #fff;
  margin: 0 0.5rem;
}
</style>
