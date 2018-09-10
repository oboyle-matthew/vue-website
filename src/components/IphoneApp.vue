<template >
  <div v-on:click="$emit('appClicked', name)" v-bind:style="appStyle">
    <p v-bind:style="textStyle">{{name}}</p>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        appStyle: {
          position: 'fixed',
          textAlign: 'center',
          top: (32 + parseInt(this.y) * 17) + 'vh',
          left: (33 + parseInt(this.x) * 12) + 'vw',
          width: '10vw',
          height: '15vh',
          display: 'table',
          opacity: 0,
          zIndex: 15
        },
        textStyle: {
          color: 'orange',
          display: 'table-cell',
          verticalAlign: 'middle',
          fontSize: '3vw'
        }
      }
    },
    props: ['name', 'link', 'x', 'y'],
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        if (y >= 10000 && y < 11500) {
          this.fadeIn(y-10100);
        }
        else if (y >= 11500) {
          this.fadeOut(y-11500);
        }
      },
      fadeIn(y) {
        this.appStyle.display = 'table';
        this.appStyle.opacity = (y/500);
      },
      fadeOut(y) {
        this.appStyle.opacity = 1 - (y/10)
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
