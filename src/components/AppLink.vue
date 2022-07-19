<template>
  <div class="link">
    <a href="https://github.com/jamespark89" target="_blank"
      ><img src="../../public/githubid.png" alt=""
    /></a>
    <a
      href="https://www.linkedin.com/in/sangkook-park-721426210/"
      target="_blank"
      ><img src="../../public/linkedinid.png" alt=""
    /></a>
    <div class="stem"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {}
  }
}
</script>

<style scoped>
.link {
  position: fixed;
  display: flex;
  flex-direction: column;
  align-items: center;
  bottom: 0;
  right: 1rem;
  z-index: 999;
}
@keyframes linkgrow {
  to {
    bottom: 120%;
  }
}
.link::before {
  content: '';
  width: 80px;
  top: -15px;
  right: 0;
  bottom: 0;
  left: -15px;
  position: absolute;
  background: var(--dark);
  animation: linkgrow 3s forwards;
  animation-delay: 2s;
}
img {
  width: 50px;
  height: 50px;
  border-radius: 0.7rem;
  background-color: #f0f0f0;
  box-shadow: 0 0px 10px 5px var(--orange);
}
.stem {
  width: 3px;
  height: 100px;
  background-color: #f0f0f0;
  box-shadow: 0 0px 10px 5px var(--orange);
}
img:hover {
  transform: scale(1.1);
  background-color: var(--orange);
}
</style>
