<template>
  <div class="h-screen bg-blue-50 flex justify-center gap-4">
    <div class="w-[55px] h-[55px] ballok bg-red-500"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
    <div class="w-[55px] h-[55px] ball bg-amber-300"></div>
  </div>
</template>

<script setup>
import {onMounted, ref} from 'vue';
import gsap from 'gsap';

onMounted(() => {
  let tl = gsap.timeline({repeat: 2, yoyo: true});

  tl.from('.ballok', {duration: 1.5, opacity: 0, scale:0.3, ease: "back"})
  tl.to('.ballok', {duration: 1, rotate: 350})
  tl.from('.ball', {duration: 1, opacity: 0, y: 150, stagger: 0.25});
  tl.addLabel('circlesOutro', "+=1")
  tl.to('.ball', {duration: 0.5, opacity: 0, x: 300, ease: "power3.out"}, "circlesOutro")
});
</script>

<style scoped>

</style>
