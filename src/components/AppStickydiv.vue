<template>
  <div id="sideDiv" class="sidebar">
    <div id="stickyDiv" :class="{ fixed: isFixed }">
      <h1>WORKS</h1>
      <ul>
        <li v-for="(project, index) in projects" :key="index">
          <a :href="'#' + projectHref(index)">{{ projects[index].title }}</a>
        </li>
      </ul>
    </div>
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
      isFixed: false,
      isActive: false,
      projects: data
    }
  },
  mounted() {
    window.addEventListener('scroll', this.getSticky)
    gsap.from('#stickyDiv', {
      scrollTrigger: {
        trigger: '#stickyDiv',
        end: 'top center',
        marker: true,
        toggleActions: 'restart none none reset'
      },

      opacity: 0,
      scale: 0.8,
      duration: 1
    })
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
    }
  }
}
</script>

<style scoped>
.sidebar {
  width: 30%;
  height: 100%;
  /* background: var(--dark); */
  display: flex;
  justify-content: center;
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
#stickyDiv > ul > li {
  font-size: 18px;
  padding: 1rem;
  margin: 1rem;
  height: 2rem;
  text-align: center;
}

#stickyDiv > ul > li > a {
  text-decoration: none;
  color: var(--lihgt);
  font-size: 1.1rem;
  padding: 0.1rem;
}

#stickyDiv > ul > li > a:hover {
  border-bottom: 3px solid var(--orange);
  transform: scale(1.2);
}
@media screen and (max-width: 700px) {
  .sidebar {
    width: 100%;
  }
  .sidebar {
    position: relative;
    height: fit-content;
  }
  #stickyDiv > ul {
    display: none;
  }
}
</style>
