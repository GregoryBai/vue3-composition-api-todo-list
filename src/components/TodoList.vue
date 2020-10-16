<template>
  <div class="list__wrapper">
    <ul class="list">
      <li class="list__item" v-bind:key="i" v-for="(todo, i) in todos">
        <h3>{{ todo.title }}</h3>
        <div class="item__line" />
        <p>{{ todo.desc }}</p>
        <p @click="removeTodo(i)" class="item__delete">delete me!</p>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: {
    todos: Array,
  },
  setup(_, ctx) {
    const removeTodo = (idx) => {
      console.log(idx)
      ctx.emit("remove-todo", idx)
    }
    return { removeTodo }
  },
}
</script>

<style lang="scss" scoped>
@import "../styles/base.scss";
.list {
  list-style: none;
}

.list__item {
  border-radius: 18px;
  border: 6px solid teal;
  padding: 10px 20px;
  display: flex;
  justify-items: center;
  align-items: center;
  flex-direction: column;
  background-color: rgba(0, 0, 0, 0.05);
  width: 500px;
  margin-bottom: 10px;
}

.item__line {
  @include line;
  background-color: teal;
}

.item__delete {
  margin-top: 10px;
  text-align: right;
  widows: 100%;
  font-size: 0.75rem;
  padding: 3px 5px;
  border-radius: 5px;
  border: 2px solid rgba(0, 0, 0, 0.2);

  &:hover {
    background-color: red;
    color: aliceblue;
  }
}
</style>
