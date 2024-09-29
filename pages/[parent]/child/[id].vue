<template>
    <div>
      <h2>Dynamic Child Page under Parent: {{ route.params.parent }} with ID: {{ route.params.id }}</h2>
    </div>
  </template>
  
  <script setup>
  import { useRoute } from 'vue-router'
  
  const route = useRoute()
  </script>
  