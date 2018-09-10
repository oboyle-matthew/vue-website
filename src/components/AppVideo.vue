<template >
  <div v-bind:style="infoStyle">
    <iframe  v-bind:style="phoneStyle"
            src="https://www.youtube.com/embed/VSRYQPMG7dg">
    </iframe>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        phoneStyle: {
          position: 'fixed',
          top: '15.5vh',
          left: '31.9vw',
          width: '36.4vw',
          height: '69.2vh',
        },
        infoStyle: {
          position: 'fixed',
          top: '25vh',
          left: '40vw',
          width: '30vw',
          height: '15vh',
          zIndex: 16
        }
      }
    },
    props: ['name']
  }
</script>

<style>
</style>
