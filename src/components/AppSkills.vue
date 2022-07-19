<template>
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
        require('../../public/vue.png'),
        require('../../public/php.png')
      ]
    }
  },
  setup() {},
  mounted() {
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
      x: 500,
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
.card {
  color: var(--light);
  position: relative;
  top: 10%;
  width: 60%;
}

h1 {
  font-size: 2rem;
}
.skills {
  margin-top: 10rem;
  overflow: hidden;
}
.skillsIcon > ul {
  display: flex;
  flex-direction: row;
  margin: 16px;
}
.skillsIcon ul > li > img {
  width: 80%;
  min-width: 50px;
}
.skills ul > li {
  width: 10vw;
  margin: 3%;
}
@media screen and (max-width: 600px) {
  .skillsIcon > ul {
    flex-wrap: wrap;
    justify-content: left;
  }
}
</style>
