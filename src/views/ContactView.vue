<template>
  <div class="contact">
    <div class="container">
      <form class="contactform" @submit.prevent="sendEmail">
        <h1>Contact Me</h1>
        <input v-model="name" name="name" placeholder="Name" required />
        <input v-model="email" name="email" placeholder="E-mail" required />
        <textarea
          v-model="message"
          name="message"
          rows="4"
          placeholder="Message "
          required
        ></textarea>
        <button type="submit">submit</button>
      </form>
    </div>
  </div>
</template>

<script>
import emailjs from '@emailjs/browser'
import ScrollTrigger from 'gsap/ScrollTrigger'
import gsap from 'gsap'
gsap.registerPlugin(ScrollTrigger)
export default {
  name: 'ContactUs',
  data() {
    return {
      name: '',
      email: '',
      message: ''
    }
  },
  mounted() {
    gsap.from('.contactform', {
      scrollTrigger: {
        trigger: '.contactform',
        end: 'top center',
        toggleActions: 'restart none none reset'
      },
      y: 100,
      opacity: 0,
      scale: 0.8,
      duration: 1
    })
  },

  computed: {},
  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm(
          'service_9f07o4m',
          'template_yokb39a',
          e.target,
          '3m7qjMNjB5xxEkPNZ',
          {
            name: this.name,
            email: this.email,
            message: this.message
          }
        )
      } catch (error) {
        console.log({ error })
        alert('Fail to send email. Please try again')
      }
      alert('The email has been sent susccessfully. Thanks!')
      // Reset form field
      this.name = ''
      this.email = ''
      this.message = ''
    }
  }
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
.container {
  width: 80%;
  height: 500px;
  display: flex;
  justify-content: center;
}
.contactform {
  background: #fff;
  width: 100%;
  max-width: 600px;
  padding: 2vw 4vw;
  position: relative;
  z-index: 1;
  display: flex;
  justify-content: center;
  flex-direction: column;
  border-radius: 10px;
}
form h1 {
  text-align: center;
  color: #555;
  font-weight: 800;
  margin-bottom: 20px;
}
form input,
form textarea {
  border: 0;
  margin: 10px 0;
  padding: 20px;
  outline: none;
  background: #f5f5f5;
}
form button {
  padding: 15px;
  background: #82dee6;
  color: var(--dark);
  font-size: 18px;
  border: 0;
  outline: none;
  cursor: pointer;
  width: 150px;
  margin: 20px atou 0;
  border-radius: 1rem;
  margin-left: auto;
}
form button:hover {
  background-color: #b8c7b9;
}
</style>
