<template>
  <div class="navbar">
    <div class="nav-item">
      <ul>
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="#works">Works</router-link></li>
        <li><router-link to="#about">About</router-link></li>
        <li><router-link to="#contact">Contact</router-link></li>
      </ul>
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
  width: 100vw;
  justify-content: end;
  padding-right: 5rem;
  z-index: 1;
  background-color: var(--dark);
  height: 52px;
  display: flex;
  align-items: center;
}
a {
  padding: 1rem;
  color: var(--light);
  text-decoration: none;
}
a:hover {
  background: var(--grey);
  border-radius: 1rem;
  color: var(--light);
}
ul {
  display: flex;
  list-style-type: none;
}
</style>
