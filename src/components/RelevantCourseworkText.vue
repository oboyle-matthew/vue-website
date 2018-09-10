<template >
  <img v-bind:style="mapStyle" src="../images/USA.png">
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
        if (y >= 6400) {
          this.mapStyle.position = 'fixed';
          this.mapStyle.top = '29vh';
        }
        else {
          this.mapStyle.position = 'absolute';
          this.mapStyle.top = '910vh';

        }
      }
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
    }
  }
</script>

<style>
</style>
