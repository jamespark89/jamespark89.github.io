<template>
  <Navbar />
  <router-view />
</template>
<script setup>
import Navbar from './components/Navbar.vue'
</script>
<style>
:root {
  --primary: #4ade80;
  --grey: #64748b;
  --dark: #1e293b;
  --light: #f1f5f9;
  --typewriterSpeed: 3s;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira sans', sans-serif;
}

body {
  background: var(--light);
}

#app {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
