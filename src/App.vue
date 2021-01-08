<template>
  <div id="app">
    <h1>Ninja reaction timer</h1>
    <ButtonPlay v-if="isShowPlay" @start="playPressed"/>
    <ButtonClick v-if="isShowClick" @clicked="testReaction"/>
    <ResultBlock v-if="isShowResult" :result="timeOfReaction"/>
    <button v-if="isShowResult" class="but rep" @click="replay">replay</button>
  </div>
</template>

<script>
import ButtonPlay from './components/ButtonPlay.vue'
import ButtonClick from "@/components/ButtonClick";
import ResultBlock from "@/components/ResultBlock";

export default {
  name: 'app',
  components: {
    ResultBlock,
    ButtonClick,
    ButtonPlay
  },
  data() {
    return {
      isShowPlay: true,
      isShowClick: false,
      isShowResult: false,
      timeOfReaction: 0,
      timerId: 0
    }
  },
  methods: {
    playPressed() {
      this.isShowPlay = false
      const time = Math.floor(Math.random()*3000+1000)
      setTimeout(() => {
        this.isShowClick = true
      }, time)
    },
    testReaction() {
      this.isShowClick = false
      this.isShowResult = true
    },
    replay() {
      this.isShowResult = false
      this.isShowPlay = true
      this.timeOfReaction = 0
    }
  },
  watch: {
    isShowClick() {

      if (this.isShowClick) {
        this.timerId = setInterval(() => this.timeOfReaction += 10, 10)
      }
      else {
        clearTimeout(this.timerId)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
