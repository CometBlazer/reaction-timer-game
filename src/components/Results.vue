<template>
  <p>Reaction time: {{ scoreName }} ms</p>
  <p class="rank">Rank: {{ rank }}</p>
</template>

<script>
export default {
    props: ['scoreName', ], 
    data() {
      return {
        rank: null
      }
    },
    mounted() { //lifecycle hook
      if(this.scoreName < 200){
        this.rank = 'Lightning fast'
      }
      else if(this.scoreName < 300){
        this.rank = 'Decent'
      }
      else{
        this.rank = 'Snail pace...'
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