<template >
  <h3 v-bind:style="textStyle">{{text}}</h3>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        textStyle: {
          fontSize: '4vw',
          left: parseInt(this.left) + 'vw',
          bottom: '11vh',
          textAlign: 'center',
          position: 'fixed',
          display: 'none',
          lineHeight: '7vh',
          zIndex: 3,
          opacity: 1,
        }
      }
    },
    props: ['text', 'left', 'scroll'],
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        var diff = y - parseInt(this.scroll);
        if (diff >= 0 && diff < 220) {
          this.scrollIn(diff);
        }
        else if (diff >= 220 && y < 7900) {
          this.stop();
        }
        else if (y >= 7900 && y < 8650) {
          this.scrollOut(y-7900)
        }
        else if (y >= 8650 && y < 9336) {
          this.stopTop();
        }
        else if (y >= 9336) {
          this.fadeOut(y-9336);
        }
        else {
          this.textStyle.display = 'none';
        }
      },
      scrollIn(y) {
        this.textStyle.bottom = ((y / 5) - 40) + "vh";
        this.textStyle.display = 'inline';
      },
      stop() {
        this.textStyle.bottom = '4vh';
        this.textStyle.display = 'inline';
      },
      scrollOut(y) {
        this.textStyle.bottom = (4 + (y / 10)) + "vh";
      },
      stopTop() {
        this.textStyle.bottom = "79vh";
        this.textStyle.color = 'black';
        this.textStyle.opacity = 1;
      },
      fadeOut(y) {
        this.textStyle.opacity = 1 - (y/200);
        this.textStyle.color = 'white';
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
