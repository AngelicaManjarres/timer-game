<template>
  <h1>How fast are you? Timer Game</h1>
  <button @click="start" :disabled="isPlaying">Start!</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/BlockComponent.vue'
import Results from './components/ResultsComponent.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  background: rgb(63, 27, 163);
  border: none;
  padding: 15px 20px;
  color: #fff;
}
button:disabled {
  background: rgb(124, 83, 236);
  color: #999;
}

</style>
