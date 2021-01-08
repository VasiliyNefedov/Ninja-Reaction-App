<template>
  <div class="button">
    <button class="but" @click="clicked">Click me!</button>
  </div>
</template>

<script>
export default {
  name: "ButtonClick",
  methods: {
    clicked() {
      this.$emit('clicked')
    }
  }
}
</script>

<style>

</style>