<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <h2>Punch it!</h2>
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0
      }
    },
    methods: {
      startTimer() {
        this.timer = setInterval(() => {
          this.reactionTime += 10
        }, 10)
      },
      stopTimer() {
        clearInterval(this.timer)
        console.log(this.reactionTime)
        this.$emit('end', this.reactionTime)
      }
    },
    mounted() {
      setTimeout(() => {
        this.showBlock = true
        this.startTimer()
        }, this.delay)
    },
    
}
</script>

<style scoped>

.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: #fff;
    text-align: center;
    padding: 50px 0;
    margin: 40px auto;
}
h2 {
  font-size: 3rem;
}

</style>