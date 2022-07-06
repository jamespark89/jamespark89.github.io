<template>
  <div class="about">
    <section class="card">
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
      <div class="skills">
        <div class="skillsHead">
          <h1>Skills</h1>
        </div>
        <div class="skillsIcon">
          <ul>
            <li v-for="(skillsimg, index) in skillsimgs" :key="index">
              <img :src="getskillsimg(index)" alt="" />
            </li>
          </ul>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import ScrollTrigger from 'gsap/ScrollTrigger'
import gsap from 'gsap'
gsap.registerPlugin(ScrollTrigger)

export default {
  data() {
    return {
      skillsimgs: [
        require('../../public/html-5.png'),
        require('../../public/css-3.png'),
        require('../../public/java-script.png'),
        require('../../public/vue.png')
      ]
    }
  },
  setup() {},
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
    gsap.from('.skillsHead', {
      scrollTrigger: {
        trigger: '.skills',
        end: 'top center',
        toggleActions: 'restart none none reset'
      },
      y: 100,
      opacity: 0,
      duration: 1
    })
    gsap.from('.skillsIcon', {
      scrollTrigger: {
        trigger: '.aboutmeMain',
        end: 'top center',
        scrub: 3,
        toggleActions: 'restart none none reset'
      },
      x: 700,
      opacity: 0
    })
  },
  methods: {
    getskillsimg: function (index) {
      return this.skillsimgs[index]
    }
  }
}
</script>

<style scoped>
.about {
  width: 100%;
  height: 100vh;
  background: -webkit-linear-gradient(to bottom, var(--dark), #6878ac);
  background: linear-gradient(to bottom, var(--dark), #6878ac);
  display: flex;
  justify-content: center;
}
.card {
  color: var(--light);
  position: relative;
  top: 10%;
  width: 60%;
}

h1 {
  font-size: 2rem;
}
.aboutmeMain > p {
  margin-top: 3rem;
  font-size: 1.2rem;
  color: #aaaaaa;
  font-family: 'Roboto Mono', monospace;
}
.skills {
  margin-top: 10rem;
}
.skillsIcon > ul {
  display: flex;
  flex-direction: row;
  margin: 16px;
}
.skills ul > li > img {
  width: 80%;
}
.skills ul > li {
  width: 10vw;
  margin: 3%;
}
</style>
