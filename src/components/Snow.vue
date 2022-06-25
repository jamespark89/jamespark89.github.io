<template>
  <div id="wrapper" class="wrapper">
    <!-- <span class="snow"></span> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      snowNumber: 200,
      snowSize: 35,
      count: '1',
      mouseX: '',
      mouseY: '',
      snowX: '',
      snowY: '',
      i: 1
    }
  },
  setup() {},
  mounted() {
    this.addSnow()
    window.addEventListener('mousemove', this.touchSnow)
  },
  methods: {
    addSnow() {
      const snow = document.createElement('span')
      snow.className = 'snow'

      snow.style.left = `${Math.random() * (window.innerWidth - 1) + 1}px`
      snow.style.animationDuration = `${Math.random() * (20 - 8) + 8}s`
      snow.style.animationDelay = `${Math.random() * (10 - 1) + 1}s`
      snow.style.opacity = `${Math.random()}`
      snow.style.width = `${Math.random() * this.snowSize}px`
      snow.style.height = snow.style.width
      const wrapper = document.getElementById('wrapper')
      wrapper.append(snow)
      if (this.count < this.snowNumber) {
        window.requestAnimationFrame(this.addSnow)

        this.count++
      }
      snow.setAttribute('id', this.i)
      this.i++
    },
    touchSnow(e) {
      let i = 1
      let snow = 0
      while (i < this.snowNumber) {
        snow = document.getElementById(i)
        this.snowX = parseInt(snow.getBoundingClientRect().x / 50)
        this.snowY = parseInt(snow.getBoundingClientRect().y / 50)
        i++
        if (
          this.snowX === parseInt(e.clientX / 50) &&
          this.snowY === parseInt(e.clientY / 50)
        ) {
          snow.style.transform = 'scale(0.6)'
          snow.style.opacity = toString(`${parseInt(snow.style.opacity) * 0.1}`)
        }
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
