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
          left: '5vw',
          width: '60vw',
          // backgroundColor: 'red',
          top: parseInt(this.top) + "vh",
          position: 'fixed',
          display: 'none',
          opacity: 1,
        }
      }
    },
    props: ['text', 'top', 'scroll'],
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        var diff = y - parseInt(this.scroll);
        if (diff >= 0 && diff < 425) {
          this.scrollIn(diff);
        }
        else if (diff >= 425 && y < 7900) {
          this.stop();
        }
        else if (y >= 7900) {
          this.moveUp(y-7900)
        }
        else {
          this.textStyle.display = 'none';
        }
      },
      scrollIn(y) {
        this.textStyle.left = ((y / 5) - 80) + "vw";
        this.textStyle.display = 'inline';
      },
      stop() {
        this.textStyle.left = '5vw';
        this.textStyle.display = 'inline';
      },
      moveUp(y) {
        this.textStyle.top = (parseInt(this.top) - (y / 10)) + "vh";
        this.textStyle.display = 'inline';
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
