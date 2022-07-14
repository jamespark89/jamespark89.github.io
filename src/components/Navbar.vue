<template>
  <div class="navbar">
    <button @click="activateNavbar">
      <img
        class="static"
        :class="{ active: ~isActive }"
        :src="require('../../public/' + pic[0] + '.png')"
        alt="pic"
      />
    </button>
    <button @click="activateNavbar">
      <img
        class="static"
        :class="{ active: isActive }"
        :src="require('../../public/' + pic[1] + '.png')"
        alt="pic"
      />
    </button>
    <div
      class="static nav-item"
      :class="{ active: isActive, deactive: ~isActive }"
    >
      <ul>
        <li><router-link @click="activateNavbar" to="/">Home</router-link></li>
        <li>
          <router-link @click="activateNavbar" to="#about">About</router-link>
        </li>
        <li>
          <router-link @click="activateNavbar" to="#works">Works</router-link>
        </li>

        <li>
          <router-link @click="activateNavbar" to="#contact"
            >Contact</router-link
          >
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isActive: false,
      pic: ['hamburger', 'X']
    }
  },
  mounted() {},
  methods: {
    activateNavbar() {
      this.isActive = ~this.isActive
    }
  }
}
</script>

<style scoped>
img {
  width: 100%;
  height: 100%;
}
button {
  width: 30px;
  height: 30px;
  background: transparent;
  border: none;
  position: fixed;
  right: 1rem;
}
button:hover {
  cursor: pointer;
}
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  justify-content: flex-end;
  z-index: 999;
  background-color: transparent;
  height: 52px;
  display: flex;
  align-items: center;
}
.nav-item {
  position: fixed;
  top: 0;
  border: 1px solid var(--light);
  border-radius: 1rem;
  background: var(--dark);
  flex-direction: column;
  margin-top: 50px;
}
ul {
  list-style-type: none;
}
ul > li {
  margin: 30px;
  font-size: 18px;
}
.static {
  display: none;
}
.active {
  display: block;
  animation: open 0.3s;
}
@keyframes open {
  from {
    right: -160px;
  }
  to {
    right: 0;
  }
}
a {
  color: var(--light);
  text-decoration: none;
  padding: 0.7rem;
  border: 2px solid var(--dark);
}
a:hover {
  border: 2px solid var(--orange);
  border-radius: 1rem;
}
</style>
