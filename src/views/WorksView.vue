<template>
  <div class="works">
    <app-stickydiv />
    <main>
      <app-projects />
    </main>
  </div>
</template>

<script>
import AppStickydiv from '@/components/AppStickydiv.vue'
import AppProjects from '@/components/AppProjects.vue'

export default {
  components: { AppStickydiv, AppProjects }
}
</script>
<style scoped>
.works {
  width: 100%;
  height: 500%;
  display: flex;
  background: -webkit-linear-gradient(to top, var(--dark), #6878ac);
  background: linear-gradient(to top, var(--dark), #6878ac);
}
main {
  width: 70%;
  height: 100%;
  /* background: var(--dark); */
}
@media screen and (max-width: 700px) {
  .works {
    flex-direction: column;
    height: auto;
  }
  main {
    width: 100%;
  }
}
</style>
