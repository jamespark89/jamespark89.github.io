<template>
  <div class="about">
    <section class="card">
      <app-aboutme />
      <app-skills />
    </section>
  </div>
</template>

<script>
import AppAboutme from '@/components/AppAboutme.vue'
import AppSkills from '@/components/AppSkills.vue'

export default {
  components: { AppAboutme, AppSkills }
}
</script>
<style scoped>
.about {
  width: 100%;
  height: 100vh;
  background: -webkit-linear-gradient(to bottom, var(--dark), #6878ac);
  background: linear-gradient(to bottom, var(--dark), #6878ac);
  display: flex;
  justify-content: center;
}
.card {
  color: var(--light);
  position: relative;
  top: 10%;
  width: 60%;
}
</style>
