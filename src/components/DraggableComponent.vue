<template>
  <div class="draggable-area">
    <div class="draggable-box" ref="dragBox"></div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import Draggable from 'gsap/Draggable';

gsap.registerPlugin(Draggable);

const dragBox = ref(null);

onMounted(() => {
  Draggable.create(dragBox.value, {
    type: "x,y",
    bounds: ".draggable-area",
    onDragEnd: function() {
      gsap.to(dragBox.value, { x: 50, y: 100, duration: 0.8, ease: "elastic.out(1, 0.3)" });
    }
  });
});
</script>

<style scoped>
.draggable-area {
  width: 100%;
  height: 300px;
  border: 2px dashed #ccc;
  position: relative;
  overflow: hidden;
}
.draggable-box {
  width: 50px;
  height: 50px;
  background-color: #2980b9;
  position: absolute;
  border-radius: 10px;
  cursor: pointer;
}
</style>
