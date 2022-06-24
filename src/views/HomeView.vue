<template>
  <div id="home" class="home">
    <h1>Hello, my name is James.</h1>
  </div>
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
  width: 100%;
  height: 100vh;
  text-align: center;

  z-index: 0;
}
.home {
  color: var(--light);
  margin-top: 48px;
  display: flex;
  justify-content: center;
}
h1 {
  position: relative;
  font-family: 'Roboto Mono', monospace;
  width: max-content;
  height: max-content;
}
h1::before,
h1::after {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

h1::before {
  background: var(--dark);
  animation: typewriter var(--typewriterSpeed) steps(24) 1s forwards;
}
h1::after {
  width: 0.125em;
  background: yellow;
  animation: typewriter var(--typewriterSpeed) steps(24) 1s forwards,
    blink 800ms steps(24) infinite;
}
@keyframes typewriter {
  to {
    left: 100%;
  }
}
@keyframes blink {
  to {
    background: transparent;
  }
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
