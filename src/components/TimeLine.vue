<template>
  <div>
    <div ref="box1" class="box">Box 1</div>
    <div ref="box2" class="box">Box 2</div>
    <div ref="box3" class="box">Box 3</div>
  </div>
</template>

<script setup>
import { gsap } from "gsap";
import { onMounted, ref } from "vue";

const box1 = ref(null);
const box2 = ref(null);
const box3 = ref(null);

onMounted(() => {
  const tl = gsap.timeline();
  tl.to(box1.value, { x: 100, opacity: 1, duration: 1 })
      .to(box2.value, { y: 100, opacity: 1, duration: 1 })
      .to(box3.value, { x: 100, y: 100, opacity: 1, duration: 1 });
});
</script>

<style>
.box {
  opacity: 0;
  transition: all 1s;
  margin: 5px;
  background-color: #42b983;
  color: white;
  padding: 20px;
  text-align: center;
}

</style>
