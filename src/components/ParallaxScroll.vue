<template>
  <div class="parallax-container">
    <!-- Background Layer -->
    <div class="parallax layer-back" style="background-color: #673AB7;"></div>
    <!-- Middle Layer -->
    <div class="parallax layer-mid" style="background-color: #3F51B5;" ref="midLayer"></div>
    <!-- Foreground Layer -->
    <div class="parallax layer-front" style="background-color: #2196F3;" ref="frontLayer"></div>
  </div>
</template>

<script setup>
import {ref, onMounted} from 'vue';
import {gsap} from 'gsap';
import {ScrollTrigger} from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

const midLayer = ref(null);
const frontLayer = ref(null);

onMounted(() => {
  // Mid layer parallax effect
  gsap.to(midLayer.value, {
    scrollTrigger: {
      trigger: '.parallax-container',
      start: "top bottom",  // When the top of the container enters the bottom of the viewport
      end: "bottom top",    // When the bottom of the container leaves the top of the viewport
      scrub: true
    },
    y: -150
  });

  // Front layer parallax effect
  gsap.to(frontLayer.value, {
    scrollTrigger: {
      trigger: '.parallax-container',
      start: "top bottom",
      end: "bottom top",
      scrub: true
    },
    y: -300
  });
});
</script>

<style scoped>
.parallax-container {
  position: relative;
  height: 150vh; /* Long enough to scroll through */
  overflow-x: hidden;
}

.parallax {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh; /* Full viewport height */
}

.layer-back {
  background-color: #673AB7; /* Deep purple */
  z-index: 1; /* Below all */
}

.layer-mid {
  background-color: #3F51B5; /* Indigo */
  z-index: 2; /* Middle layer */
}

.layer-front {
  background-color: #2196F3; /* Blue */
  z-index: 3; /* Top layer */
}
</style>
