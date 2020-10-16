<template>
  <Header />
  <main class="wrapper">
    <Menu @add-todo="submitTodo" />
    <TodoList :todos="state" @remove-todo="removeTodo" />
  </main>
</template>

<script>
import TodoList from "./components/TodoList"
import Header from "./components/Header"
import Menu from "./components/Menu"
import { ref, watch } from "vue"

export default {
  name: "App",
  setup() {
    const state = ref([])

    watch(state, () => {
      console.log(state.value)
    })

    function submitTodo(todo) {
      state.value.push(todo)
    }

    const removeTodo = (idx) => {
      console.log(idx)
      state.value = state.value.filter((todo, i) => i !== idx)
    }
    return { state, submitTodo, removeTodo }
  },
  components: {
    TodoList,
    Header,
    Menu,
  },
}
</script>

<style lang="scss">
@import "./styles/base.scss";

.wrapper {
  margin: 20px;
  display: flex;
  justify-content: space-evenly;
}
</style>
