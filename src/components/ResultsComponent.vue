<template>
  <p> Your score is: {{score}}ms </p>
  <p class="rank" :class="color"> {{rank}} </p>
</template>

<script>
export default {
    props: ['score'],
    data() {
      return {
        rank: null,
        color: null
      }
    },
    mounted() {
      if(this.score < 300) {
        this.rank = "Way to go, Flash!!"
        this.color = "green"
      } else if(this.score >= 300 && this.score < 400) {
        this.rank = "Fast reflexes!"
        this.color = "blue"
      } else if(this.score >= 400 && this.score < 600) {
        this.rank = "Good job, but you could do better!"
        this.color = "red"
      } else {
        this.rank = "Too slow!"
        this.color = "red"
      }
    }

}
</script>

<style scoped>
.rank {
  font-size: 1.5rem;
  font-weight: 600;
  letter-spacing: 5px;
}
.green {
  color: green
}
.blue {
  color:blue;
}
.red {
  color: crimson;
}

</style>