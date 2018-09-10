<template >
  <h3 v-bind:style="textStyle">{{text}}</h3>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        text: ".",
        textStyle: {
          fontSize: '4vw',
          left: (10 - parseInt(this.num))*1.5 + 62 + 'vw',
          bottom: '4vh',
          textAlign: 'center',
          position: 'fixed',
          lineHeight: '7vh',
          zIndex: 3,
          opacity: 1
        }
      }
    },
    props: [ 'newText', 'num'],
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        var diff = y - 7500;
        if (diff >= 0 && diff < 220) {
          this.scrollIn(diff)
        }
        else if (diff >= 220 && y < 7900) {
          this.stop();
        }
        else if (y >= 7900 && y < 8100 + parseInt(this.num)*100 ) {
          this.moveUp(y-7900);
        }
        else if (y >= 8100 + parseInt(this.num)*100) {
          if (y >= 8740 + parseInt(this.num) * 47) {
            this.fadeOut(y - (8740 + parseInt(this.num) * 47))
          }
          else {
            this.textStyle.color = 'black';
            this.textStyle.opacity = 1;
          }
          this.moveDown(y-7900, y - (8100 + parseInt(this.num)*100));
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
      moveUp(y) {
        this.text=".";
        this.textStyle.fontSize="4vw";
        var bottom = Math.min(79, 4 + (y / 10));
        this.textStyle.bottom = bottom + "vh";
      },
      moveDown(old, y) {
        var start = Math.min(79, (4 + (old / 10)));
        this.textStyle.bottom = start - (y/8) + "vh";
        if (y > 100) {
          this.text = this.newText;
          this.textStyle.fontSize="1.5vw";
        } else {
          this.text=".";
          this.textStyle.fontSize="4vw";
        }
      },
      fadeOut(y) {
        this.textStyle.opacity = 1 - (y/150);
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
