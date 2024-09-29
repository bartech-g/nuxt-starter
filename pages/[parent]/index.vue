<template>
    <div>
      <h1>Dynamic Parent Page - Parent: {{ route.params.parent }}</h1>
      <nuxt-link :to="`/${route.params.parent}/child`">Go to Child</nuxt-link>
      <nuxt-link :to="`/${route.params.parent}/child/1`">Go to Child with ID 1</nuxt-link>
      <nuxt-link :to="`/${route.params.parent}/child/2`">Go to Child with ID 2</nuxt-link>
  
      <!-- This is where the nested page will be rendered -->
      <NuxtPage />
    </div>
  </template>
  
  <script setup>
  import { useRoute } from 'vue-router'
  
  const route = useRoute()
  </script>
  