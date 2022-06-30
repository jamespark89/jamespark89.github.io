<template>
  <div class="about">
    <section class="card">
      <h1>About Me</h1>
      <p>
        Hi, I'm a front-end developer based on Australia.<br />
        I'm interested in making value with technologies.<br />
      </p>
      <h1>Skills</h1>
      <div class="skills">
        <ul>
          <li><img src="../../public/html-5.png" alt="" /></li>
          <li><img src="../../public/css-3.png" alt="" /></li>
          <li><img src="../../public/java-script.png" alt="" /></li>
          <li><img src="../../public/vue.png" alt="" /></li>
        </ul>
      </div>
      <span>more about :</span>

      <button>Download resume</button>
    </section>
  </div>
</template>

<script>
export default {}
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
.card > h1,
p,
button {
  margin: 1rem;
}
.card > h1 {
  font-size: 2rem;
  margin-top: 3rem;
}
.card > p {
  font-size: 1.5rem;
}
.skills > ul {
  display: flex;
  flex-direction: row;
  margin: 16px;
}
.skills ul > li > img {
  width: 80%;
}
.skills ul > li {
  width: 10vw;
  margin: 3%;
}
</style>
