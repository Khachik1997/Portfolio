<template>
  <div class="app-layout min-h-screen">
    <nav class="nav">
        <div class="flex gap-4">
          <router-link to="/">Home</router-link>
          <router-link to="/about">Portfolio</router-link>
        </div>
        <div class="flex gap-4">
          <p>Button1</p>
          <p>Button2</p>
        </div>
    </nav>
    <router-view/>
  </div>
</template>

<script setup>

</script>

<style>
.app-layout {
  width: 100%;
  padding: 16px 0px;
  background: url("@/assets/svgs/background.svg") center;
}

.nav {
  background-color: #212528;
  color: white;
  padding: 16px 56px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin-bottom: 20px;
  -webkit-box-shadow: 0px 2px 9px 3px rgba(0,0,0,0.75);
  -moz-box-shadow: 0px 2px 9px 3px rgba(0,0,0,0.75);
  box-shadow: 0px 2px 9px 3px rgba(0,0,0,0.75);
}
</style>
