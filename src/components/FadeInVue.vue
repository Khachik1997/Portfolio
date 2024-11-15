<template>
  <div ref="box" style="opacity: 0; transition: opacity 1s;">
    <h1>Hello, animate Fade IN(1)</h1>
  </div>
</template>

<script setup>
import { gsap } from "gsap";
import { onMounted, ref } from "vue";

const box = ref(null);

onMounted(() => {
  gsap.to(box.value, { opacity: 1, duration: 1 });
});
</script>
