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
        <!-- <ul>
          <li v-for="(project, index) in 5" :key="index">
            <div :id="projectHref(index)" :class="projectHref(index)"></div>
          </li>
        </ul> -->
        <div id="project1" class="project1"></div>
        <div id="project2" class="project1"></div>
        <div id="project3" class="project1"></div>
        <div id="project4" class="project1"></div>
        <div id="project5" class="project1"></div>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isFixed: false,
      isActive: false
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
    }
  }
}
</script>
<style scoped>
.works {
  width: 100vw;
  height: 500vh;
  background: var(--light);
  display: flex;
}
.sidebar {
  width: 30vw;
  height: 100%;
  background: var(--dark);
  display: flex;
  justify-content: center;
}
main {
  width: 70vw;
  height: 100%;
  background: var(--dark);
}
.fixed {
  position: sticky;
  top: 50px;
}
#stickyDiv {
  height: fit-content;
  margin-top: 1rem;
  color: var(--light);
}
.hide {
  display: none;
}
h1 {
  text-align: center;
}
.projects {
  display: flex;
  flex-direction: column;
}
.projects > div {
  width: 100%;
  height: 100vh;
}
</style>
