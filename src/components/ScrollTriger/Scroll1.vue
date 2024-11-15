<template>
<div class="bg-black flex flex-col px-[400px] gap-y-[600px] py-[1200px]">
  <div class="box-scroll a">a</div>
  <div class="box-scroll b">b</div>
  <div class="box-scroll c">c</div>
</div>
</template>

<script setup>
import { gsap } from "gsap";
import {ScrollTrigger} from "gsap/ScrollTrigger";
import { onMounted, ref } from "vue";

gsap.registerPlugin(ScrollTrigger);

onMounted(()=> {

  let tl = gsap.timeline({
    scrollTrigger: {
      trigger: ".c",
      start: "top 700px",
      end: "top 200px",
      markers: true,
      scrub: true,
      pin: true
    }
  })

  tl.to(".c", {
    x: 1200,
    rotate: 360,
    duration: 3
  })
})

</script>

<style scoped>
.box-scroll {
  width: 150px;
  height: 150px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: black;
  font-weight: 800;
  font-size: 32px;
}

.a {
  background: #673AB7;
}

.b {
  background: #42b983;
}

.c {
  background: coral;
}
</style>
