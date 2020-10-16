<template>
  <header class="header" :class="{ 'header--red': isRed }" @click="toggleColor">
    <h1 class="header__heading">Welcome to the App</h1>
  </header>
</template>
<script>
import { ref } from "vue"
export default {
  name: "Header",
  setup() {
    const isRed = ref(false)

    function toggleColor() {
      isRed.value = !isRed.value
    }

    return { isRed, toggleColor }
  },
}
</script>
<style lang="scss" scoped>
.header {
  -webkit-user-select: none;
  -moz-user-select: none;
  margin: 0 20px;
  border-bottom: 5px solid rgba(0, 0, 0, 0.4);
  border-bottom-left-radius: 60px;
  border-bottom-right-radius: 60px;
  color: aliceblue;
  letter-spacing: 3px;
  word-spacing: 7px;
  height: 7vh;
  background-color: teal;
  display: flex;
  align-items: center;
  justify-content: center;

  &--red {
    background-color: rgba(240, 60, 60, 0.7);
  }
}
</style>
