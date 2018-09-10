<template >
  <div>
    <Dot num="10" newText="Statistics"/>
    <Dot num="9" newText="Linear Algebra"/>
    <Dot num="8" newText="Introduction to Computer Science (Python)"/>
    <Dot num="7" newText="Data Structure and Algorithms (Java)"/>
    <Dot num="6" newText="Discrete Math for Compsci (Scheme)"/>
    <Dot num="5" newText="Computer Architecture (C)"/>
    <Dot num="4" newText="Web Application Development (Vue.js)"/>
    <Dot num="3" newText="Software Design/Implementation (Java)"/>
    <Dot num="2" newText="Design/Analysis of Algorithms"/>
    <Dot num="1" newText="Delivering Software"/>
    <Dot num="0" newText="Database Systems"/>

  </div>

</template>

<script>
  import Dot from './Dot';

  export default {
    name: 'app',
    components: {
      Dot
    }
  }
</script>

<style>
</style>
