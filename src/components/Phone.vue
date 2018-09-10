<template >
  <div>
    <div v-bind:style="container">
      <img v-bind:style="phoneStyle" src="../images/phone.png">
    </div>
    <PhoneBackground/>
    <div v-if="!singleProject">
      <Time/>
      <IphoneApp v-on:appClicked="showProject" name="Fact Check" x="0" y="0"/>
      <IphoneApp v-on:appClicked="showProject" name="Vooga" x="1" y="0"/>
      <IphoneApp v-on:appClicked="showProject" name="Game" x="2" y="0"/>
      <IphoneApp v-on:appClicked="showProject" name="Code Quality" x="0" y="1"/>
      <IphoneApp v-on:appClicked="showProject" name="Trello" x="1" y="1"/>
      <IphoneApp v-on:appClicked="showProject" name="Slogo" x="2" y="1"/>
      <IphoneApp v-on:appClicked="showProject" name="xPACE" x="0" y="2"/>
      <IphoneApp v-on:appClicked="showProject" name="Dots" x="1" y="2"/>
      <IphoneApp v-on:appClicked="showProject" name="Offline Map" x="2" y="2"/>
    </div>
    <div v-else>
      <BackButton v-on:backClicked="reset"/>
      <AppVideo v-bind:name="showing"/>
      <AppInfo v-bind:name="showing"/>
    </div>


  </div>
</template>

<script>
  import PhoneBackground from './PhoneBackground';
  import Time from './Time';
  import IphoneApp from './IphoneApp';
  import BackButton from './BackButton';
  import AppInfo from './AppInfo';
  import AppVideo from './AppVideo';

  export default {
    name: 'app',
    data () {
      return {
        singleProject: false,
        showing: '',
        container: {
          backgroundColor: 'red',
          position: 'absolute',
          top: '1300vh',
          left: 0,
          width: '100vw',
          height: '750vh',
          overflow: 'hidden'
        },
        phoneStyle: {
          position: 'relative',
          top: '-100vh',
          left: '-100vw',
          width: '400vw',
          height: '400vh',
          transform: 'rotate(0deg)'
        }
      }
    },
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        if (y >= 9500 && y < 10000) {
          this.focusPhone((y-9400) / 6);
        }
        else if (y >= 10000 && y < 11500) {
          this.stop();
        }
        else if (y >= 11500 && y < 12950) {
          this.rotate(y-11500);
        }
        else if (y >= 12950) {
          this.leaveLeft(y-12850)
        }
        else {
          this.phoneStyle.position = 'relative';
          this.phoneStyle.top = '-100vh';
          this.phoneStyle.left = '-100vw';
          this.phoneStyle.width = '400vw';
          this.phoneStyle.height = '400vh';
        }
      },
      focusPhone(y) {
        this.phoneStyle.position = 'fixed';
        this.phoneStyle.top = (y - 100) + 'vh';
        this.phoneStyle.left = ((y * (122.5/100)) - 100) + 'vw';
        this.phoneStyle.width = (400 - (y * (345 / 100))) + 'vw';
        this.phoneStyle.height = (400 - (y * (300 / 100))) + 'vh';
      },
      stop() {
        this.phoneStyle.position = 'fixed';
        this.phoneStyle.top = 0;
        this.phoneStyle.left = "22.5vw";
        this.phoneStyle.width = "55vw";
        this.phoneStyle.height = "100vh";
        this.phoneStyle.transform = 'rotate(0deg)'
      },
      showProject(name) {
        this.singleProject = true;
        this.showing = name;
      },
      reset() {
        this.singleProject = false;
      },
      rotate(y) {
        this.phoneStyle.transform = 'rotate(-' + (Math.min(90, y / 15)).toString() + 'deg)'
        this.phoneStyle.left = "22.5vw";
      },
      leaveLeft(y) {
        this.phoneStyle.transform = 'rotate(-90deg)';
        this.phoneStyle.left = 22.5 + y/18 + "vw";
      }
    },
    components: {
      PhoneBackground,
      Time,
      IphoneApp,
      BackButton,
      AppInfo,
      AppVideo
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
      this.updateScroll();
    }
  }
</script>

<style>
</style>
