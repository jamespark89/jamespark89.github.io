<template>
  <div id="wrapper" class="wrapper">
    <!-- <span class="snow"></span> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: '0'
    }
  },
  mounted() {
    this.addSnow()
  },
  methods: {
    addSnow() {
      const snow = document.createElement('span')
      snow.className = 'snow'
      snow.style.left = `${Math.random() * (window.innerWidth - 1) + 1}px`
      snow.style.animationDuration = `${Math.random() * (20 - 8) + 8}s`
      snow.style.animationDelay = `${Math.random() * (10 - 1) + 1}s`
      snow.style.opacity = `${Math.random()}`
      snow.style.width = `${Math.random() * 15}px`
      snow.style.height = snow.style.width
      const wrapper = document.getElementById('wrapper')
      wrapper.append(snow)
      if (this.count < 300) {
        window.requestAnimationFrame(this.addSnow)
        console.log('add')
        this.count++
      }
    }
  }
}
</script>

<style>
.snow {
  background-image: url(../assets/snow.png);
  background-size: contain;
  position: absolute;
  display: block;
  top: -10%;
  /* background: snow; */
  z-index: 1;
  border-radius: 100%;
  filter: blur(1px);
  animation: snowfall infinite;
  animation-timing-function: linear;
}

@keyframes snowfall {
  from {
    top: -10px;
  }
  to {
    top: 99%;
    opacity: 0;
  }
}
.wrapper {
  position: absolute;
  width: 100vw;
  height: 100vh;
  background: var(--dark);
}
</style>
