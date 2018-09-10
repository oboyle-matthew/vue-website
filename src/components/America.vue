<template >
  <div>
    <img v-bind:style="mapStyle" src="../images/USA.png">
  </div>

</template>

<script>

  export default {
    name: 'app',
    data () {
      return {
        mapStyle: {
          height: '45vh',
          width: '55vw',
          left: '5vw',
          position: 'absolute',
          opacity: 1,
          top: '910vh'
        }
      }
    },
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        if (y >= 6400 && y < 7900) {
          this.mapStyle.position = 'fixed';
          this.mapStyle.top = '29vh';
        }
        else if (y >= 7900) {
          this.moveUp(y - 7900);
        }
        else {
          this.mapStyle.position = 'absolute';
          this.mapStyle.top = '910vh';

        }
      },
      moveUp(y) {
        this.mapStyle.top = (29 - (y / 10)) + "vh";
      }
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
    }
  }
</script>

<style>
</style>
