<template>
  <div class="contact">
    <app-contactform />
  </div>
</template>

<script>
import AppContactform from '@/components/AppContactform.vue'
export default {
  components: { AppContactform },
  name: 'ContactUs'
}
</script>

<style scoped>
.contact {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: -webkit-linear-gradient(to bottom, var(--dark), #6878ac);
  background: linear-gradient(to bottom, var(--dark), #6878ac);
}
@media screen and (max-width: 600px) {
  .contact {
    height: 80vh;
    justify-content: initial;
  }
}
</style>
