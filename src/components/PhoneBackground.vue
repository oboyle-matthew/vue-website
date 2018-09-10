<template >
  <img v-bind:style="backgroundStyle" src="../images/background.jpg" />
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        backgroundStyle: {
          position: 'fixed',
          top: '15.5vh',
          left: '31.9vw',
          width: '36.4vw',
          height: '69.2vh',
          display: 'none',
          opacity: 0
        }
      }
    },
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        if (y >= 10000 && y < 11500) {
          this.fadeIn(y-10100);
        }
        else if (y >= 11500) {
          this.fadeOut(y-11500);
        }
        else {
          this.backgroundStyle.display = 'none';
        }
      },
      fadeIn(y) {
        this.backgroundStyle.display = 'inline';
        this.backgroundStyle.opacity = (y/500);
      },
      fadeOut(y) {
        this.backgroundStyle.opacity = 1 - (y/10)
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
