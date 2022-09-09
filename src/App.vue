<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/product">Product Detail</RouterLink>
      <RouterLink to="/login">Login</RouterLink>
      <RouterLink to="/profile">Profile</RouterLink>
    </nav>

  </header>

  <RouterView />
</template>

<style scoped>

</style>
