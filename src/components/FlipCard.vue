<template>
  <div class="flip-card" @click="toggleFlip">
    <div :class="{'do-flip': isFlipped}" class="flip-card-inner">
      <div class="flip-card-front">
        Click me to flip!
      </div>
      <div class="flip-card-back">
        Hello, I'm the back!
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { gsap } from 'gsap';

const isFlipped = ref(false);

function toggleFlip() {
  isFlipped.value = !isFlipped.value;
  const element = document.querySelector('.flip-card-inner');
  if (isFlipped.value) {
    gsap.to(element, { rotationY: 180, duration: 0.6, ease: "power2.inOut" });
  } else {
    gsap.to(element, { rotationY: 0, duration: 0.6, ease: "power2.inOut" });
  }
}
</script>

<style scoped>
.flip-card {
  background-color: transparent;
  width: 300px;
  height: 200px;
  perspective: 1000px; /* Perspective for 3D effect */
}
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
}
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden; /* Elements not visible when facing away */
}
.flip-card-front {
  background-color: #bbb;
  color: black;
}
.flip-card-back {
  background-color: #2980b9;
  color: white;
  transform: rotateY(180deg); /* Flipped by default */
}
</style>
