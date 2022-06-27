<template>
  <Navbar />
  <router-view />
  <WorksView id="works" />
  <AboutView id="about" />
  <ContactView id="contact" />
</template>
<script setup>
import Navbar from './components/Navbar.vue'
import WorksView from './views/WorksView.vue'
import AboutView from './views/AboutView.vue'
import ContactView from './views/ContactView.vue'
</script>
<style>
:root {
  --primary: #4ade80;
  --grey: #64748b;
  --dark: #1e293b;
  --light: #f1f5f9;
  --typewriterSpeed: 3s;
  --typewriterCount: 24;
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
</style>
