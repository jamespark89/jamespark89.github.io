<template>
  <div class="works">
    <aside id="sideDiv" class="sidebar">
      <div id="stickyDiv" :class="{ fixed: isFixed }">
        <h1>works</h1>
        <!-- <ul>
          <li><a href="#project1">Porject1</a></li>
          <li><a href="#project2">Porject2</a></li>
          <li><a href="#project3">Porject3</a></li>
          <li><a href="#project4">Porject4</a></li>
          <li><a href="#project5">Porject5</a></li>
        </ul> -->
        <ul>
          <li v-for="(project, index) in 5" :key="index">
            <a :href="'#' + projectHref(index)">Project{{ index + 1 }}</a>
          </li>
        </ul>
      </div>
    </aside>
    <main>
      <section class="projects">
        <ul>
          <li v-for="(project, index) in projects" :key="index">
            <div :id="projectHref(index)" :class="projectHref(index)">
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
                  <a href=""><img src="../assets/logo.png" alt="" /></a>
                  <a href=""><img src="../assets/logo.png" alt="" /></a>
                </div>
              </div>
            </div>
          </li>
        </ul>
        <!-- <div id="project1" class="project1"></div>
        <div id="project2" class="project1"></div>
        <div id="project3" class="project1"></div>
        <div id="project4" class="project1"></div>
        <div id="project5" class="project1"></div> -->
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
          src: require('../assets/logo.png'),
          title: 'Portfolio',
          description: 'PortfolioWeb',
          skills: 'Vue.js'
        },
        {
          src: require('../assets/logo.png'),
          title: 'Portfolio',
          description: 'PortfolioWeb',
          skills: 'Vue.js'
        },
        {
          src: require('../assets/logo.png'),
          title: 'Portfolio',
          description: 'PortfolioWeb',
          skills: 'Vue.js'
        },
        {
          src: require('../assets/logo.png'),
          title: 'Portfolio',
          description: 'PortfolioWeb',
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
  height: 500vh;
  background: var(--light);
  display: flex;
}
.sidebar {
  width: 30%;
  height: 100%;
  background: var(--dark);
  display: flex;
  justify-content: center;
}
main {
  width: 70%;
  height: 100%;
  background: var(--dark);
}
.fixed {
  position: sticky;
  top: 20%;
}
#stickyDiv {
  height: fit-content;
  margin-top: 1rem;
  color: var(--light);
}
.hide {
  display: none;
}
#stickyDiv > h1 {
  text-align: center;
  font-size: 30px;
  margin-bottom: 2rem;
}

.projects {
  display: flex;
  flex-direction: column;
  background-color: var(--dark);
}
ul > li {
  font-size: 18px;
  padding: 1rem;
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
  height: 80%;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(7.3px);
  -webkit-backdrop-filter: blur(7.3px);
  border: 1px solid rgba(255, 255, 255, 0.37);
  text-align: center;
}
.projectCard > div {
  margin: 10px;
}
.projectThumbnail {
  overflow: hidden;
  height: 70%;
  display: flex;
  justify-content: center;
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(7.3px);
  -webkit-backdrop-filter: blur(7.3px);
  border: 1px solid rgba(255, 255, 255, 0.37);
}
.usedSkills,
.projectTitle,
.projectDescription {
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(7.3px);
  -webkit-backdrop-filter: blur(7.3px);
  border: 1px solid rgba(255, 255, 255, 0.37);
  height: 5%;
}
.projectThumbnail > img {
  min-width: 1000px;
  width: 100%;
  height: 100%;
}
.projectLink {
  width: 48px;
  height: 48px;
  display: flex;
  justify-content: center;
}
.projectLink > a {
  padding: 0;
  width: 40px;
}
.projectLink > a > img {
  width: 100%;
  height: 100%;
}
@media screen and (max-width: 600px) {
  .works {
    flex-direction: column;
  }
  .sidebar,
  main {
    width: 100%;
  }
  #stickyDiv > ul {
    display: none;
  }
  .projectCard {
    width: 100%;
  }
}
</style>
