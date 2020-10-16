<template>
  <aside class="menu">
    <h2 class="menu__header">@Menu</h2>
    <div class="menu__line" />
    <label for="menu__inputTitle">Title:</label>
    <input
      v-model="todoTitle"
      type="text"
      id="menu__inputTitle"
      class="menu__inputTitle"
    />
    <label for="menu__inputDescription">Description:</label>
    <textarea
      id="menu__inputDescription"
      v-model="todoDesc"
      @keydown.enter="submitTodo($event)"
      placeholder="What to do..."
      class="menu__inputDescription"
    ></textarea>
  </aside>
</template>
<script>
import { ref } from "vue"
export default {
  setup(props, ctx) {
    const todoTitle = ref("")
    const todoDesc = ref("")

    function submitTodo(e) {
      if (todoTitle.value !== "" && todoDesc.value !== "") {
        const todo = { title: todoTitle.value, desc: todoDesc.value }
        todoTitle.value = e.target.value
        todoTitle.value = ""
        todoDesc.value = ""
        ctx.emit("add-todo", todo)
      }
    }

    return { todoDesc, todoTitle, submitTodo }
  },
}
</script>

<style lang="scss">
@import "../styles/base.scss";
.menu {
  align-self: start;
  border-radius: 40px;
  width: 30vw;
  margin: 0px 20px;
  padding: 30px;
  background-color: teal;
  color: aliceblue;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}

.menu__header {
  margin-bottom: 10px;
}

.menu__line {
  @include line;
}

.menu__inputTitle {
  padding: 8px 16px;
  border-radius: 14px;
  text-align: center;
  border: none;
  margin-bottom: 10px;

  &:focus {
    outline: none;
  }
}

.menu__inputDescription {
  margin-bottom: 10px;
  overflow: hidden;
  min-height: 30px;
  max-height: 200px;
  min-width: 70%;
  max-width: 90%;
  padding: 8px 16px;
  border-radius: 25px;
  text-align: center;

  &:focus {
    outline: none;
  }
}
</style>
