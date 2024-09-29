<template>
    <div class="section container mx-auto p-5">
      <!-- <PhotoGallery title="My Photo Gallery">
          <template #hero>
            <img src="https://picsum.photos/200" alt="" width="300">
          </template>
  </PhotoGallery> -->
      <BaseListing v-model:itemList="listItems" title="Base Listing Component"
        url="https://jsonplaceholder.typicode.com/todos">
        <template v-slot:section="{ child }">
          Length: {{ child.length }}
        </template>
        <template v-slot:list>
            <NuxtPage />
          <ul>
            <li v-for="todo in filteredTodos" :key="todo.id">
              <input type="checkbox" :checked="todo.completed">
              <NuxtLink :to="`/about/${todo.id}`"> {{ todo.title }}</NuxtLink>
            </li>
          </ul>
        </template>
      </BaseListing>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { ref, computed } from "vue";
  import { useRoute } from 'vue-router'
  interface Todo {
    id: number;
    title: string;
    completed: boolean;
  }
  const listItems = ref<Todo[]>([])
  
  const route = useRoute()
  
  
  const filteredTodos = computed(() => {
    if (route.query.completed === 'true') {
      return listItems.value.filter((item) => item.completed)
    } else {
      return listItems.value
    }
  })
  
  
  </script>
  
  
  <style scoped lang="scss">
  .section {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }
  </style>