<template>
  <div class="button">
    <button class="but" @click="startGame">Play</button>
  </div>
</template>

<script>
export default {
  name: 'ButtonPlay',
  methods: {
    startGame() {
      this.$emit('start')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
