<template >
  <img v-bind:style="mapStyle" src="../images/ireland.png">
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        mapStyle: {
          height: '60vh',
          width: '30vw',
          left: '23vw',
          position: 'absolute',
          bottom: 50,
          opacity: 1,
          top: '285vh'
        }
      }
    },
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        if (y >= 1850 && y < 5400) {
          this.stay();
        }
        else if (y >= 5400) {
          this.fadeOut(y - 5400);
        }
        else {
          this.mapStyle.position = "absolute";
          this.mapStyle.top = "285vh";
        }

      },
      stay() {
        this.mapStyle.position = "fixed";
        this.mapStyle.top = "30vh";
      },
      fadeOut(y) {
        this.mapStyle.opacity = 1 - (y/100);
      }
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
      this.updateScroll();
    }
  }
</script>

<style>
</style>
