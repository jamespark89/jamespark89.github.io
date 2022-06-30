<template>
  <div class="works">
    <aside id="sideDiv" class="sidebar">
      <div id="stickyDiv" :class="{ fixed: isFixed }">
        <h1>works</h1>
        <ul>
          <li v-for="(project, index) in projects" :key="index">
            <a :href="'#' + projectHref(index)">{{ projects[index].title }}</a>
          </li>
        </ul>
      </div>
    </aside>
    <main>
      <section class="projects">
        <ul>
          <li v-for="(project, index) in projects" :key="index">
            <div
              class="project"
              :id="projectHref(index)"
              :class="projectHref(index)"
            >
              <div class="projectCard">
                <div class="projectThumbnail">
                  <img :src="getprojectThumbnail(index)" alt="" />
                </div>
                <div class="projectTitle">
                  {{ projects[index].title }}
                </div>
                <div class="projectDescription">
                  {{ projects[index].description }}
                </div>
                <div class="usedSkills">{{ projects[index].skills }}</div>
                <div class="projectLink">
                  <a href=""><img src="../../public/demo.png" alt="" /></a>
                  <a href=""><img src="../../public/github.png" alt="" /></a>
                </div>
              </div>
            </div>
          </li>
        </ul>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isFixed: false,
      isActive: false,
      projects: [
        {
          src: require('../../public/portfolio.png'),
          title: 'Fronted Portfolio Website',
          description: 'Fronted Portfolio Website',
          skills: 'Vue.js'
        },
        {
          src: require('../../public/portfolio.png'),
          title: 'Project2',
          description: 'Project2',
          skills: 'Vue.js'
        },
        {
          src: require('../../public/portfolio.png'),
          title: 'Project3',
          description: 'Project3',
          skills: 'Vue.js'
        }
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.getSticky)
  },
  unmounted() {
    window.removeEventListener('scroll', this.getSticky)
  },
  methods: {
    getSticky() {
      const stickyDiv = document.getElementById('stickyDiv')
      // const stickyTop = stickyDiv.getBoundingClientRect().y
      const stickyDivBottom = stickyDiv.getBoundingClientRect().bottom
      const sideDiv = document.getElementById('sideDiv')
      const sideDivBottom = sideDiv.getBoundingClientRect().bottom
      const sideDivTop = sideDiv.getBoundingClientRect().y

      if (
        stickyDivBottom < sideDivBottom ||
        window.screenY > sideDivTop - 27.5
      ) {
        this.isFixed = true
      } else {
        this.isFixed = false
      }
    },
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
.works {
  width: 100%;
  height: 300vh;
  display: flex;
  background: -webkit-linear-gradient(to top, var(--dark), #6878ac);
  background: linear-gradient(to top, var(--dark), #6878ac);
}
.sidebar {
  width: 30%;
  height: 100%;
  /* background: var(--dark); */
  display: flex;
  justify-content: center;
}
main {
  width: 70%;
  height: 100%;
  /* background: var(--dark); */
}
.fixed {
  position: sticky;
  top: 20%;
}
.hide {
  display: none;
}
#stickyDiv {
  height: fit-content;
  padding-top: 1rem;
  margin-top: 1rem;
  color: var(--light);
}

#stickyDiv > h1 {
  text-align: center;
  font-size: 30px;
  margin-bottom: 2rem;
}
#stickyDiv > ul > li > a {
  text-decoration: none;
  color: var(--lihgt);
  font-size: 1.2rem;
}
#stickyDiv > ul > li {
  font-size: 18px;
  padding: 1rem;
  margin: 1rem;
  text-align: center;
}
a:hover {
  transform: scale(1.1) !important;
}
.projects {
  height: 100%;
  display: flex;
  flex-direction: column;
  /* background-color: var(--dark); */
}

.projects > ul > li > div {
  width: 100%;
  height: 100vh;
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
@media screen and (max-width: 700px) {
  .works {
    flex-direction: column;
  }
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
  .project {
    height: auto !important;
  }
  .projectCard {
    width: 90%;
    margin: 1rem;
  }
}
</style>
