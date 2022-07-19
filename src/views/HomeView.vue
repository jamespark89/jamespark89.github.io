<template>
  <div id="home" class="home">
    <div class="hello">
      <h1>Hello, I'm James.</h1>
    </div>
    <p>Front-end developer</p>
    <app-link />
  </div>
</template>

<script>
import AppLink from '@/components/AppLink.vue'

export default {
  components: { AppLink },
  name: 'HomeView'
}
</script>

<style scoped>
.home {
  color: var(--light);
  height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  background: var(--dark); /* fallback for old browsers */
}
h1 {
  margin-top: 30vh;
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
  font-size: 2rem;
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
    font-size: 20px;
  }
  p {
    font-size: 18px;
  }
}
</style>
