<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="bg-dark p-3">
      <nav class="d-flex align-items-center justify-content-center gap-5">
        <RouterLink to="/" class="text-decoration-none text-white px-3 p-2 text-uppercase">Home</RouterLink>
        <RouterLink to="/" class="text-decoration-none text-white px-3 p-2 text-uppercase">about</RouterLink>
        <RouterLink to="/" class="text-decoration-none text-white px-3 p-2 text-uppercase">list</RouterLink>
        <RouterLink to="/" class="text-decoration-none text-white px-3 p-2 text-uppercase">favourite</RouterLink>
      </nav>
  </header>

  <RouterView />
</template>
