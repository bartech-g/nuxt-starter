<template>
    <div>
      <h2>Child Page under Parent: {{ route.params.parent }}</h2>
    </div>
  </template>
  
  <script setup>
  import { useRoute } from 'vue-router'
  
  const route = useRoute()
  </script>
  