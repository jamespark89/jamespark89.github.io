<template>
  <Snow />
  <div id="home" class="home">
    <h1>Hello, my name is James.</h1>
    <p>Front-end developer</p>
  </div>
</template>

<script>
import Snow from '@/components/Snow.vue'
export default {
  name: 'HomeView',
  components: { Snow }
}
</script>

<style scoped>
.home {
  color: var(--light);
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: row;
  justify-content: center;
  z-index: -1;
  background: var(--dark);
}
h1 {
  margin-top: 30vh;
  position: absolute;
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
  animation: typewriter var(--typewriterSpeed) steps(var(--typewriterCount)) 1s
    forwards;
}
h1::after {
  width: 0.125em;
  background: yellow;
  animation: typewriter var(--typewriterSpeed) steps(var(--typewriterCount)) 1s
      forwards,
    blink 800ms steps(var(--typewriterCount)) infinite;
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
p {
  position: absolute;
  margin-top: 42vh;
  font-size: 24px;
  font-family: 'Roboto', sans-serif;
  animation: slideup 5s;
}
@keyframes slideup {
  0% {
    opacity: 0;
  }
  70% {
    opacity: 0;
    top: 20%;
  }
  100% {
    opacity: 1;
    top: 0;
  }
}
@media screen and (max-width: 600px) {
  h1 {
    display: none;
  }
}
</style>
