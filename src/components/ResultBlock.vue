<template>
<div class="result">
  <h2>{{stringResult}}</h2>
  <p>Your result {{result}}ms!</p>
</div>
</template>

<script>
export default {
  name: "ResultBlock",
  props: {
    result: Number
  },
  data() {
    return {
      stringResult: 'nothing...'
    }
  },
  mounted() {
    if (this.result < 330) {
      this.stringResult = 'You are a real ninja!'
    }
    else if (this.result < 500) {
      this.stringResult = 'You need to train more!'
    }
    else {
      this.stringResult = 'You slow as a turtle!'
    }
  },
  methods: {
    replay() {
      this.$emit('replay')
    }
  }}
</script>

<style>

</style>