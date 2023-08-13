<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" v-bind:disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" v-bind:delay="delay"/>
</template>

<script>

import Block from './components/Block.vue'

export default {
  name: 'App',
  components: {
    Block,

  },
  data() {
    return {
      isPlaying: false,
      delay: null, //set it to a random number

    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000; //in milliseconds - random amount between 2000 and 7000 ms
      this.isPlaying = true;
      console.log(this.delay)
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
  color: #444;
  margin-top: 60px;
}
</style>
