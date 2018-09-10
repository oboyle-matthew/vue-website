<template >
  <div v-bind:style="backgroundStyle">
    <p v-bind:style="timeStyle">{{hours}}:{{minutes}}:{{seconds}}</p>
    <p v-bind:style="dateStyle">{{day}}, {{month}} {{date}}</p>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        hours: 0,
        minutes: 0,
        seconds: 0,
        day: '',
        month: '',
        date: '',
        timeStyle: {
          fontSize: '5vw',
          position: 'relative',
          top: '-6.5vh'
        },
        dateStyle: {
          fontSize: '1.5vw',
          position: 'relative',
          top: '-15.5vh'
        },
        backgroundStyle: {
          color: 'white',
          textAlign: 'center',
          position: 'fixed',
          top: '14vh',
          left: '31.9vw',
          width: '36.4vw',
          height: '69.2vh',
          display: 'none',
          opacity: 0
        }
      }
    },
    mounted () {
      this.updateTime();
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
      updateTime() {
        var d = new Date();
        var hours = d.getHours();
        this.hours = hours < 10 ? "0" + hours : hours;
        var mins = d.getMinutes();
        this.minutes = mins < 10 ? "0" + mins : mins;
        var secs = d.getSeconds();
        this.seconds = secs < 10 ? "0" + secs : secs;
        var days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
        this.day = days[d.getDay()];
        var months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
        this.month = months[d.getMonth()];
        this.date = d.getDate();
      },
      fadeOut(y) {
        this.backgroundStyle.opacity = 1 - (y/10)
      }
    },

    mounted() {
      this.updateTime();
      this.updateScroll();
      window.addEventListener('scroll', this.updateScroll);
      setInterval(this.updateTime, 1000);
    }
  }
</script>

<style>
</style>
