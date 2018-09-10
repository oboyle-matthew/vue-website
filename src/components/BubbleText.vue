<template>
  <div v-bind:style="textStyle">
    <p id="bubble_text">{{text}}</p>
  </div>

</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        textStyle: {
          display: 'none',
          position: 'fixed',
          left: '49.5vw',
          top: '28vh',
          width: '15vw',
          height: '11vh',
          opacity: 1,
          textAlign: 'center',
          // backgroundColor: 'red',
          zIndex: 5
        }
      }
    },
    props: ['text', 'scroll'],
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        var diff = y - parseInt(this.scroll);
        if (diff >= -1000 && diff < 280) {
          this.textStyle.display = 'table';
          this.textStyle.position = 'fixed';
          this.textStyle.left = (79.5 - (diff / 10)) + "vw";
          this.textStyle.top = '28vh';
        } else if (diff >= 280 && diff < 1000) {
          this.textStyle.display = 'table';
          this.textStyle.left = "51.5vw";
          this.textStyle.opacity = 1 - ((diff - 280) / 500);
        }
        else {
          this.textStyle.display = 'none';
        }

      }
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
    }
  }
</script>

<style>
  #bubble_text {
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    font-size: 1.5vw;
  }
</style>
