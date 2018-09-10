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
          width: '25vw',
          // backgroundColor: 'red',
          top: '11vh',
          wordSpacing: '100vw',
          textAlign: 'center',
          position: 'fixed',
          display: 'none',
          lineHeight: '7vh',
          opacity: 1,
        }
      }
    },
    props: ['text', 'left', 'scroll'],
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        var diff = y - parseInt(this.scroll);
        if (diff >= 0 && diff < 500) {
          this.scrollIn(diff);
        }
        else if (diff >= 500 && y < 7900) {
          this.stop();
        }
        else if (y >= 7900) {
          this.scrollOut(8900 - y)
        }
        else {
          this.textStyle.display = 'none';
        }
      },
      scrollIn(y) {
        this.textStyle.top = ((y / 5) - 80) + "vh";
        this.textStyle.display = 'inline';
      },
      stop() {
        this.textStyle.top = '20vh';
        this.textStyle.display = 'inline';
      },
      scrollOut(y) {
        this.textStyle.top = ((y / 10) - 80) + "vh";
        this.textStyle.display = 'inline';
      }
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
    }
  }
</script>

<style>
</style>
