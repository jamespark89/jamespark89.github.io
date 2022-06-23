<template>
  <div id="home" class="home">Home</div>
  <div id="works" class="works">Works</div>
  <div id="about" class="about">About</div>
  <div id="contact" class="contact">Contact</div>
</template>

<script>
export default {
  name: 'HomeView',
  components: {}
}
</script>
<style scoped>
div {
  background: var(--dark);
  width: 100vw;
  height: 920px;
  text-align: center;
  font-size: 10rem;
  z-index: 0;
}
.home {
  margin-top: 48px;
}
.works {
  background: var(--light);
}
.about {
  background: var(--dark);
}
.contact {
  background: var(--light);
}
</style>
