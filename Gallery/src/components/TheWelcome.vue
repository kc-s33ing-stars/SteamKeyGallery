<script setup>
import WelcomeItem from './WelcomeItem.vue';

// Manually list the filenames of the images in your Images folder
const images = [
  "image1.jpg",
  "image2.jpg",
  "image3.jpg",
  "image4.jpg",
  "image5.jpg",
  "image6.jpg",
  "image7.jpg",
  "image8.jpg",
  "image9.png",
  "image10.jpg",
  "image11.jpg",
  "image12.png",
  "image27.jpg",
  "image14.jpg",
  "image15.jpg",
  "image16.jpg",
  "image17.jpg",
  "image18.jpg",
  "image19.jpg",
  "image20.jpg",
  "image21.jpg",
  "image23.jpg",
  "image24.jpg",
  "image25.png",
  "image26.jpg",
  "image27.jpg",
  "image28.jpg",
  "image29.jpg"
];
</script>

<template>
  <div class="gallery">
    <WelcomeItem v-for="(image, index) in images" :key="index" :image="image" />
  </div>
</template>

<style scoped>
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 10px;
  padding: 20px;
}
</style>
