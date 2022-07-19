<template>
  <Navbar />
  <Snow />
  <router-view />
  <AboutView id="about" />
  <WorksView id="works" />
  <ContactView id="contact" />
</template>
<script setup>
import Snow from '@/components/Snow.vue'
import Navbar from './components/Navbar.vue'
import WorksView from './views/WorksView.vue'
import AboutView from './views/AboutView.vue'
import ContactView from './views/ContactView.vue'
</script>
<style>
html {
  scroll-behavior: smooth;
}

:root {
  --primary: #6ac98d;
  --grey: #64748b;
  --dark: #1e293b;
  --light: #f1f5f9;
  --orange: rgb(248, 205, 124);
  --typewriterSpeed: 3s;
  --typewriterCount: 17;
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

ul {
  list-style-type: none;
}
</style>
