<template>
  <p v-if=!tooSoon >Reaction time: {{ scoreName }} ms</p>
  <p class="rank" >{{ rank }}</p>
</template>

<script>
export default {
    props: ['scoreName', ], 
    data() {
      return {
        rank: null,
        tooSoon: false,
      }
    },
    mounted() { //lifecycle hook
      if(this.scoreName == -1){
        this.rank = 'Too soon! (Try again)'
        this.tooSoon = true
      }
      else{
        this.tooSoon = false

        if(this.scoreName < 200){
          this.rank = 'Lightning fast!'
        }
        else if(this.scoreName < 400){
          this.rank = 'You\'re average.'
        }
        else{
          this.rank = 'Bro, get faster...'
        }
      }
    }
}
</script>

<style>
  .rank{
    font-size: 1.4em;
    color: rgb(15, 163, 153);
    font-weight: bold;
  }
</style>