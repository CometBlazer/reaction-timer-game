<template>
  <div class="block" v-if="showBlock" @click="stopTimer()">
    Click me
  </div>
  <div class="block2" v-else @click="tooSoon()">
    Wait for green
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0,
      }
    },
    mounted() {
      // console.log('component mounted');
      setTimeout(() => {
        this.showBlock = true;
        // console.log(this.showBlock);
        this.startTimer()
      }, this.delay);
    },
    methods: {
      startTimer(){
        this.timer = setInterval(() => {
            this.reactionTime += 10
        }, 10);
      },
      stopTimer(){
        clearInterval(this.timer); //this.timer = setInterval(() => { will no longer rum
        // console.log(this.reactionTime);
        this.$emit('end', this.reactionTime);
      },
      tooSoon() {
        this.reactionTime = -1;
        this.stopTimer();
      }
    }
}
</script>

<style>
  p{
    font-weight: bold;
  }
    .block{
        width: 400px;
        border-radius: 20px;
        background: rgb(15, 163, 153);
        color: white;
        text-align: center;
        font-weight: bold;
        padding: 100px 0;
        margin: 40px auto;
        font-size: 20px;
    }
    .block2{
        width: 400px;
        border-radius: 20px;
        background: rgb(235, 47, 47);
        color: white;
        text-align: center;
        font-weight: bold;
        padding: 100px 0;
        margin: 40px auto;
        font-size: 20px;
    }
</style>