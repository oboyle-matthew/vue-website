<template >
  <img v-bind:style="planeStyle" src="../images/airplane.png">
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        planeStyle: {
          height: '4vh',
          width: '8vw',
          position: 'fixed',
          display: 'none',
          left: '0vw',
          bottom: 50,
          top: '30vh',
          transform: 'rotate(-10deg)'
        }
      }
    },
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        if (y >= 500 && y < 2000) {
          this.backgroundPlane(y - 500);
        }
        else if (y >= 5200 && y < 6400) {
          this.irelandToUS(y - 5200);
        }
        else if (y >= 6400) {
          this.dropOff(y - 6450);
        }
        else {
          this.planeStyle.display = 'none';
        }
      },
      backgroundPlane(y) {
        this.planeStyle.display = 'inline';
        this.planeStyle.left = (y/10 - 30) + "vw";
        this.planeStyle.top = (40 - y/25) + "vh";
        this.planeStyle.height = '4vh';
        this.planeStyle.width = "8vw";
        this.planeStyle.transform = 'rotate(-10deg)'
      },
      irelandToUS(y) {
        this.planeStyle.zIndex = 7;
        this.planeStyle.display = 'inline';
        this.planeStyle.left = (y/5 - 30) + "vw";
        this.planeStyle.top = (60 - y/9) + "vh";
        this.planeStyle.height = '25vh';
        this.planeStyle.width = "40vw";
        this.planeStyle.transform = 'rotate(0deg)';
      },
      dropOff(y) {
        this.planeStyle.position = 'fixed';
        this.planeStyle.top = '5vh';
        this.planeStyle.left = (y / 4) + "vw";
        this.planeStyle.width = "8vw";
        this.planeStyle.height = '4vh';

      }
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
    }
  }
</script>

<style>
</style>
