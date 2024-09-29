<template>
  <nav>
    <div class="container mx-auto px-4 py-2 flex justify-between">
      <NuxtLink to="/" class="text-2xl font-bold">Home</NuxtLink>
      <div class="flex">
        <NuxtLink to="/about?completed=true" class="px-4 py-2 hover:bg-gray-200 rounded-md">About</NuxtLink>
        <NuxtLink to="/contact" class="px-4 py-2 hover:bg-gray-200 rounded-md">Contact</NuxtLink>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">

</script>

<style scoped></style>