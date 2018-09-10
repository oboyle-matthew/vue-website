<template >
  <div>
    <div v-bind:style="leftStyle">
      <h1 v-bind:style="nameStyle">{{name}}</h1>
      <span v-bind:style="l1Style">Language: </span><span v-bind:style="l2Style">{{language}}</span><br/>
      <span v-bind:style="d1Style">Date: </span><span v-bind:style="d2Style">{{date}}</span>
      <p v-bind:style="infoStyle">{{info}}</p>
      <a v-bind:href="info" v-bind:style="repoStyle">Repository</a>
    </div>
    <div v-bind:style="rightStyle">
      <h1 v-bind:style="homeStyle">Press the home button to return to other projects</h1>
    </div>
  </div>
</template>

<script>
  import Info from '../data/AppInfo';

  export default {
    name: 'app',
    data () {
      return {
        leftStyle: {
          textAlign: 'center',
          position: 'fixed',
          top: '5vh',
          left: '2vw',
          width: '26vw',
          spacing: '10vh',
          lineHeight: '13vh'
        },
        nameStyle: {
          fontSize: '5vw'
        },
        l1Style: {
          fontWeight: 'bold',
          fontSize: '2vw'
        },
        l2Style: {
          fontSize: '1.5vw'
        },
        d1Style: {
          fontWeight: 'bold',
          fontSize: '2vw'
        },
        d2Style: {
          fontSize: '1.5vw'
        },
        infoStyle: {
          lineHeight: '3vh'
        },
        rightStyle: {
          textAlign: 'center',
          position: 'fixed',
          top: '83.5vh',
          left: '72vw',
          width: '25vw',
          height: '15vh',
          zIndex: 16
        },
        homeStyle: {
          fontSize: '2vw'
        }
      }
    },
    computed: {
      info() {
        return Info["apps"][this.name].info;
      },
      language() {
        return Info["apps"][this.name].language;
      },
      date() {
        return Info["apps"][this.name].date;
      },
      repo() {
        return Info["apps"][this.name].repo;
      }
    },
    props: ['name']
  }
</script>

<style>
</style>
