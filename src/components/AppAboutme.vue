<template>
  <div>
    <div class="aboutme">
      <div class="aboutmeHead">
        <h1>About Me</h1>
      </div>
      <div class="aboutmeMain">
        <p>
          Hi, I'm a
          <b style="color: var(--light)">front-end developer</b> based on
          Melbourne.<br />
          I love to making value with
          <b style="color: var(--light)">web development.</b><br />
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import ScrollTrigger from 'gsap/ScrollTrigger'
import gsap from 'gsap'
gsap.registerPlugin(ScrollTrigger)

export default {
  mounted() {
    gsap.from('.aboutmeHead', {
      scrollTrigger: {
        trigger: '.aboutme',
        end: 'top center',
        toggleActions: 'restart none none reset'
      },
      y: 100,
      opacity: 0,
      duration: 1
    })
    gsap.from('.aboutmeMain', {
      scrollTrigger: {
        trigger: '.aboutme',
        scrub: 3,
        end: 'top center',
        toggleActions: 'restart none none reset'
      },
      x: -500,
      opacity: 0
    })
  }
}
</script>

<style scoped>
.aboutmeMain > p {
  margin-top: 3rem;
  font-size: 1.2rem;
  color: #aaaaaa;
  font-family: 'Roboto Mono', monospace;
  overflow: hidden;
}
</style>
