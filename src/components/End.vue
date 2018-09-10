<template >
  <div v-bind:style="endStyle">
    <!--<a href="../images/airplane.png">Download</a>-->
    <h1 v-bind:style="thanksStyle">Thanks for visiting my page!</h1>
    <img v-bind:style="gitStyle" src="../images/github.png"/>
    <img v-bind:style="linkedStyle" src="../images/linkedin.png"/>
    <img v-bind:style="resumeStyle" src="../images/resume.png"/>
    <img v-bind:style="emailStyle" src="../images/email.png"/>

  </div>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        thanksStyle: {
          position: 'absolute',
          top: '10vh',
          fontSize: '4vw',
          width: '100vw',
          left: 0,
          textAlign: 'center'
        },
        gitStyle: {
          position: 'absolute',
          top: '30vh',
          width: '20vw',
          height: '30vh',
          left: '25vw',
        },
        linkedStyle: {
          position: 'absolute',
          top: '30vh',
          width: '25vw',
          height: '30vh',
          left: '50vw',
        },
        resumeStyle: {
          position: 'absolute',
          top: '65vh',
          width: '20vw',
          height: '30vh',
          left: '25vw',
        },
        emailStyle: {
          position: 'absolute',
          top: '57.5vh',
          width: '25vw',
          height: '45vh',
          left: '50vw',
        },
        endStyle: {
          position: 'absolute',
          backgroundColor: '#0099ff',
          top: '2050vh',
          left: 0,
        }
      }
    }
  }
</script>

<style>
</style>
