<script setup>
import { ref, onMounted } from 'vue';

// Receive image filename as a prop
defineProps({
  image: String
});

// Generate a random price between $0.10 and $20.00
const price = ref('$0.00');
const backgroundColor = ref('#ffffff');

onMounted(() => {
  // Generate random price
  const randomPrice = (Math.random() * (20 - 0.1) + 0.1).toFixed(2);
  price.value = `$${randomPrice}`;

  // Generate a random color in hex format
  backgroundColor.value = getRandomColor();
});

// Function to get the correct image URL
function getImageUrl(image) {
  return new URL(`./Images/${image}`, import.meta.url).href;
}

// Function to generate a random color
function getRandomColor() {
  const letters = '6789ABCDEF'; // Avoid very light colors
  let color = '#';
  for (let i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * letters.length)];
  }
  return color;
}
</script>

<template>
  <div class="welcome-item" :style="{ backgroundColor }">
    <img :src="getImageUrl(image)" :alt="image" class="welcome-image" />
    <div class="item-info">
      <p class="price">{{ price }}</p>
    </div>
  </div>
</template>

<style scoped>
.welcome-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 12px;
  padding: 15px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s ease-in-out;
}

.welcome-item:hover {
  transform: scale(1.05);
}

.welcome-image {
  width: 100%;
  height: auto;
  max-width: 200px;
  border-radius: 8px;
}

.item-info {
  margin-top: 10px;
  text-align: center;
}

.price {
  font-size: 18px;
  font-weight: bold;
  color: #ffffff; /* White price text for contrast */
}
</style>
