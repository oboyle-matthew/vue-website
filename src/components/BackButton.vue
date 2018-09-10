<template >
  <p v-on:click="$emit('backClicked')" v-bind:style="backStyle"></p>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        backStyle: {
          position: 'fixed',
          top: '84vh',
          left: '46vw',
          width: '8vw',
          height: '7vh',
          zIndex: 16
        }
      }
    }
  }
</script>

<style>
</style>
