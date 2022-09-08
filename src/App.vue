<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/product">Product Detail</RouterLink>
    </nav>

  </header>

  <RouterView />
</template>

<style scoped>

</style>
