<template>
  <div class="sequence-container">
    <div v-for="(item, index) in items" :key="index" class="item" :ref="addToRefs">
      {{ item.content }}
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';

const items = ref([
  { content: "Step 1: Welcome!" },
  { content: "Step 2: Learn the basics." },
  { content: "Step 3: Try it yourself." },
  { content: "Step 4: Master the skills." }
]);

const itemRefs = ref([]);

const addToRefs = el => {
  if (el) itemRefs.value.push(el);
};
console.log(itemRefs.value)

onMounted(() => {
  gsap.from(itemRefs.value, {
    opacity: 0,
    x: -100,
    stagger: 0.5,
    duration: 1,
    ease: "power2.out"
  });
});
</script>

<style scoped>
.sequence-container {
  padding: 20px;
}
.item {
  opacity: 1;
  margin: 10px;
  background-color: #2980b9;
  color: white;
  padding: 20px;
  border-radius: 8px;
}
</style>
