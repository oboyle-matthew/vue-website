<template >
  <img v-bind:style="personStyle" src="../images/avatar.png">
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        personStyle: {
          height: '20vh',
          width: '10vw',
          position: 'fixed',
          left: '45vw',
          top: '25vh',
          opacity: 1,
          zIndex: 3
        }
      }
    },
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        this.personStyle.opacity = 1;
        if (y < 500) {
          this.initialPos();
        }
        if (y >= 500 && y < 1500) {
          this.drop(y - 500);
        }
        else if (y >= 1500 && y < 1850) {
          this.stickToIreland();
        }
        else if (y >= 1850 && y < 5500) {
          this.stay();
        }
        else if (y >= 5300 && y < 6643) {
          this.fadeOut(y - 5300);
        }
        else if (y >= 6643 && y < 6870) {
          this.dropOff(y - 6643);
        }
        else if (y >= 6870 && y < 7900) {
          this.stickToAmerica();
        }
        else if (y >= 7900) {
          this.scrollUp(y-7900);
        }
      },
      initialPos() {
        this.personStyle.height = "20vh";
        this.personStyle.width = "10vw";
        this.personStyle.position = "fixed";
        this.personStyle.left = "45vw";
        this.personStyle.top = "25vh";
      },
      drop(y) {
        var width = (10 - y / 200);
        this.personStyle.position = "fixed";
        this.personStyle.top = (25 + y/17) + "vh";
        this.personStyle.left = (50 - (width/2)) + "vw";
        this.personStyle.width = width + "vw";
        this.personStyle.height = (width*2) + "vh";
      },
      stickToIreland() {
        this.personStyle.top = "290vh";
        this.personStyle.position = "absolute";
      },
      stay() {
        this.personStyle.position = "fixed";
        this.personStyle.top = "35vh";
      },
      fadeOut(y) {
        this.personStyle.opacity = 1 - (y/40);
      },
      dropOff(y) {
        this.personStyle.height = '4vh';
        this.personStyle.width = '2vw';
        this.personStyle.left = '52vw';
        this.personStyle.zIndex = (y < 100) ? 1 : 10;
        this.personStyle.top = 6 + (y / 5) + 'vh';
      },
      stickToAmerica() {
        this.personStyle.top = '51.4vh';
        this.personStyle.left = '52vw';
        this.personStyle.zIndex = 10;
      },
      scrollUp(y) {
        this.personStyle.top = (51.4 - (y / 10)) + "vh";
      }

  },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
    }
  }
</script>

<style>
</style>
