<template>
  <div id="app">
    <Person />
    <Plane />
    <div v-bind:style="ireland">
      <WelcomeText/>
      <Ireland/>
      <SpeechBubble/>
    </div>
    <div v-bind:style="america">
      <America/>
    </div>
    <div v-bind:style="ireland">
      <America/>
    </div>
    <TextFromLeft top="7" text="In 2016 I moved to North Carolina" scroll="6800" />
    <TextFromAbove left="70" text="To study computer science at Duke University" scroll="7100" />
    <TextFromBelow left="5" text="My relevant coursework includes" scroll="7500" />
    <Dots/>
    <Phone/>
    <End/>
  </div>
</template>

<script>
  import Person from './components/Person'
  import WelcomeText from './components/WelcomeText'
  import Plane from './components/Plane'
  import Ireland from './components/Ireland';
  import SpeechBubble from './components/SpeechBubble';
  import America from './components/America';
  import TextFromLeft from './components/TextFromLeft';
  import TextFromAbove from './components/TextFromAbove';
  import TextFromBelow from './components/TextFromBelow';
  import Dots from './components/Dots';
  import Phone from './components/Phone';
  import End from './components/End';



  export default {
  name: 'app',
  data () {
    return {
      ireland: {
        backgroundColor: '#0099ff',
        height: '850vh'
      },
      america: {
        backgroundColor: 'green',
        height: '450vh'
      },
      welcome: {
        color: 'white',
        position: 'absolute',
        left: 0,
        right: 0,
        textAlign: 'center',
        top: '55vh'
      }
    }
  },
  components: {
    Person,
    WelcomeText,
    Plane,
    Ireland,
    SpeechBubble,
    America,
    TextFromLeft,
    TextFromAbove,
    TextFromBelow,
    Dots,
    Phone,
    End
  }
}
</script>

<style>
</style>
