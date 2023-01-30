<template>
  <div class="projects">
    <ul>
      <li v-for="(project, index) in projects" :key="index">
        <div
          class="project"
          :id="projectHref(index)"
          :class="projectHref(index)"
        >
          <div class="projectCard">
            <div class="projectThumbnail">
              <img :src="projects[index].src" alt="" />
              <!-- <img :src="require('../../public/movieapp.png')" alt="" /> -->
            </div>
            <div class="projectTitle">
              {{ projects[index].title }}
            </div>
            <div class="projectDescription">
              {{ projects[index].description }}
            </div>
            <div class="usedSkills">{{ projects[index].skills }}</div>
            <div class="projectLink">
              <a :href="projects[index].liveLink" target="_blank"
                ><img src="../../public/demo.png" alt=""
              /></a>
              <a :href="projects[index].githubLink" target="_blank"
                ><img src="../../public/github.png" alt=""
              /></a>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import data from '../../static/projects.json'
import ScrollTrigger from 'gsap/ScrollTrigger'
import gsap from 'gsap'
gsap.registerPlugin(ScrollTrigger)

export default {
  data() {
    return {
      projects: data
    }
  },
  mounted() {
    for (let i = 1; i < this.projects.length + 1; i++) {
      gsap.from('.project' + i, {
        scrollTrigger: {
          trigger: '.project' + i,
          end: 'top center',
          toggleActions: 'restart none none none'
        },
        scale: 0.8,
        opacity: 0,
        duration: 1
      })
    }
  },
  methods: {
    projectHref: function (index) {
      return 'project' + (index + 1).toString()
    },
    getprojectThumbnail: function (index) {
      return this.projects[index].src
    }
  }
}
</script>

<style scoped>
a:hover {
  transform: scale(1.1);
}
.projects {
  height: 100%;
  display: flex;
  flex-direction: column;
  /* background-color: var(--dark); */
}

.projects > ul > li > div {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}
.projectCard {
  margin-top: 10%;
  position: relative;
  width: 80%;
  height: 700px;
  text-align: center;
}
.projectCard > div {
  margin: 10px;
  padding: 0.3rem;
  overflow: hidden;
  display: flex;
  justify-content: center;
}
.projectThumbnail {
  height: 70%;
  padding: 0 !important;
  border-radius: 0.5rem;
}

.projectThumbnail > img {
  height: 100%;
}
.projectLink {
  max-height: fit-content;
  display: flex;
  justify-content: space-between;
}
.projectLink > a {
  padding: 0;
  width: 100px;
}
.projectLink > a > img {
  position: relative;
  width: 40%;
  height: 100%;
}
.projectDescription {
  font-family: 'Lato', sans-serif;
  color: var(--light);
}
.usedSkills {
  font-family: 'Lato', sans-serif;
  color: var(--grey);
}
.projectTitle {
  font-family: 'Lato', sans-serif;
  font-size: 1.5rem;
  font-weight: bold;
  /* color: var(--dark); */
  color: var(--orange);
}
@media screen and (max-width: 700px) {
  .sidebar,
  main {
    width: 100%;
  }
  .sidebar {
    position: relative;
    height: fit-content;
  }
  #stickyDiv > ul {
    display: none;
  }
  .projects > ul > li > div {
    height: 60vh;
  }
  .projectCard {
    width: 90%;
    margin: 1rem;
    height: 50%;
  }
}
</style>
