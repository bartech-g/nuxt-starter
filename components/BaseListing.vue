<template>
    <div>
        <h2>{{ title }}</h2>
        <slot name="section" :child="itemList"></slot>
        <!-- <ul v-for="(item, index) in itemList" :key="index">
            <li>{{ item }}</li>
        </ul> -->
        <slot name="list"></slot>
    </div>
</template>

<script setup lang="ts">

import { defineEmits, defineProps, ref, onMounted } from 'vue';

// const items = ref([])

const props = defineProps({
    title: {
        type: String,
        default: '',
        required: false
    },
    url: {
        type: String,
        default: '',
        required: false
    },
    itemList: {
        type: Array,
        default: () => [],
        required: false
    }
})
const route = useRoute()
const emits = defineEmits(['update:itemList'])

function fetchItems() {
    fetch(props.url)
        .then(res => res.json())
        .then(data => {
            emits('update:itemList', data)
        })
}

onMounted(() => {
    if (props.url) {
        fetchItems()
    }
})
</script>

<style scoped></style>