<template >
  <div>
    <div v-bind:style="bubbleStyle">
      <div class="bubble">

      </div>
    </div>
    <BubbleText text="Hi There!" scroll="2800"/>
    <BubbleText text="My name is Matthew O'Boyle" scroll="3600"/>
    <BubbleText text="I'm a software engineer from Northern Ireland" scroll="4400"/>

  </div>
</template>

<script>
  import BubbleText from './BubbleText';

  export default {
    name: 'app',
    data () {
      return {
        bubbleStyle: {
          display: 'none',
          position: "fixed",
          left: '51vw',
          top: '27vh',
          opacity: 0,
          zIndex: 4
        }
      }
    },
    methods: {
      updateScroll() {
        var y = window.scrollY * 726 / window.innerHeight;
        if (y >= 1900 && y < 4800) {
          this.fadeIn(y - 1900);
        } else if (y >= 4800) {
          this.fadeOut(y - 4800)
        }
        else {
          this.bubbleStyle.opacity = 0;
        }

      },
      fadeIn(y) {
        this.bubbleStyle.display = "table";
        this.bubbleStyle.opacity = (y / 1000)
      },
      fadeOut(y) {
        this.bubbleStyle.display = "table";
        this.bubbleStyle.opacity = 1 - (y / 500);
      }
    },

    mounted() {
      window.addEventListener('scroll', this.updateScroll);
    },
    components: {
      BubbleText
    }
  }
</script>

<style>
  .bubble
  {
    width: 16vw;
    height: 13vh;
    background: #FFFFFF;
    -webkit-border-radius: 1vw;
    -moz-border-radius: 1vw;
    border-radius: 1vw;
  }

  .bubble:after
  {
    content: '';
    position: absolute;
    border-style: solid;
    border-width: 1vw 1vw 1vw 0;
    border-color: transparent #FFFFFF;
    display: table;
    width: 0;
    z-index: 1;
    left: -0.4vw;
    top: 7.5vh;
  }
</style>
