<template>
    <div>
        <h2>{{ title }}</h2>
        <slot name="hero"></slot>
        <div class="photoGallery">
            <p>Number of photos: {{ numberOfPhotos }}</p>
            <img v-for="(photo, index) in photoGallery" :key="index" :src="photo.thumbnailUrl" alt="">
        </div>
    </div>
</template>

<script lang="ts" setup>
import { defineProps, computed, ref, onMounted } from "vue";

interface Photo {
    thumbnailUrl: string;
    // Add other properties as needed
}

const photoGallery = ref<Photo[]>([]);
const numberOfPhotos = computed(() => {
    return photoGallery.value.length
})

defineProps({
    title: {
        type: String,
        default: 'Photo Gallery',
        required: false
    }
})

function fetchPhotoGallery() {
    fetch('https://jsonplaceholder.typicode.com/photos')
        .then(res => res.json())
        .then(data => {
            photoGallery.value = data
            console.log(photoGallery.value);
        })
}
onMounted(() => {
    fetchPhotoGallery()
})
</script>