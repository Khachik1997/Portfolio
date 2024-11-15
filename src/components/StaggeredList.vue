<template>
  <div class="card-container">
    <!-- Bind ref in v-for directly using a method to push each element -->
    <div v-for="(item, index) in cards" :key="index" :ref="addToRefs" class="card">
      {{ item.title }}
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';

const cards = [
  { title: 'Card 1', content: 'Content for card 1.' },
  { title: 'Card 2', content: 'Content for card 2.' },
  { title: 'Card 3', content: 'Content for card 3.' },
  { title: 'Card 4', content: 'Content for card 4.' },
  { title: 'Card 5', content: 'Content for card 5.' }
];

const cardsRefs = ref([]);

const addToRefs = (el) => {
  if (el) {
    cardsRefs.value.push(el);
  }
};

onMounted(() => {
  gsap.from(cardsRefs.value, {
    opacity: 0,
    rotation: -90,
    y: 50,
    stagger: 0.1,
    ease: "power2.out",
    duration: 0.8
  });
});
</script>

<style>
.card-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
.card {
  width: 200px;
  height: 250px;
  margin: 10px;
  padding: 20px;
  background-color: #f9f9f9;
  border: 1px solid #e1e1e1;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  transform-origin: bottom center;
}

</style>
