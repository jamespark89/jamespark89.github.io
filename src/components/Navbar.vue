<template>
  <div class="navbar">
    <div class="nav-item">
      <router-link to="/">Home</router-link>
      <router-link to="#works">Works</router-link>
      <router-link to="#about">About</router-link>
      <router-link to="#contact">Contact</router-link>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  justify-content: end;
  padding-right: 5rem;
  z-index: 999;
  background-color: var(--light);
  height: 48px;
  display: flex;
  align-items: center;
}
a {
  padding: 1rem;
  color: var(--dark);
  text-decoration: none;
}
a:hover {
  background: var(--grey);
  border-radius: 1rem;
  color: var(--light);
}
</style>
