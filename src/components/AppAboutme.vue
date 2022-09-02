<template>
  <div>
    <div class="aboutme">
      <div class="aboutmeHead">
        <h1>ABOUT ME</h1>
      </div>
      <div class="aboutmeMain">
        <p>
          Hi, I'm a
          <b style="color: var(--light)">front-end developer</b> based in
          Melbourne.<br />
        </p>
        <p>
          I love to create values with
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
h1 {
  font-size: 2rem;
}
.aboutmeMain {
  margin-top: 2rem;
}
.aboutmeMain > p {
  margin-top: 0.5rem;
  font-size: 1.2rem;
  color: #aaaaaa;
  font-family: 'Open Sans', sans-serif;
  overflow: hidden;
}
</style>
