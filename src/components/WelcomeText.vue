<template >
  <div v-bind:style="welcome">
    <h1>Welcome to my web page!</h1>
    <p>Scroll down to view</p>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        welcome: {
          color: 'white',
          position: 'absolute',
          left: 0,
          right: 0,
          textAlign: 'center',
          top: '50vh',
          // fontSize: '30vw',
          opacity: (100 - window.scrollY) / 100
        }
      }
    },

    methods: {
      updateScroll() {
        this.welcome.opacity = (100 - window.scrollY) / 100
      }
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
    }
  }
</script>

<style>
  h1 {
     font-size: 2.5vw;
  }
  p {
    font-size: 1.5vw;
  }
</style>
