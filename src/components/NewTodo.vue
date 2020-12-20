<template>
  <ul>
    <li v-for="(item, index) in todos" :key="item.newTodo">
      <h3 :class="{ done: item.done }" @click="isDone(item)">
        {{ item.content }}
      </h3>
      <button @click="remove(todos, index)">Remove</button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todos: String,
  },
  setup() {
    const isDone = (item) => {
      item.done = !item.done;
    };
    const remove = (todos, index) => {
      todos.splice(index, 1);
    };
    return {
      remove,
      isDone,
    };
  },
};
</script>

<style>
.done {
  text-decoration: line-through;
  color: #ccc;
}

ul {
  list-style: none;
  padding: 0;
  max-width: 100%;
}
li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 2px solid #374e63;
}

h3:hover {
  cursor: pointer;
}

button {
  padding: 0.3rem 1rem;
  font-size: 1rem;
  border: none;
  outline: none;
  font-weight: 600;
}
button:hover {
  cursor: pointer;
  background: #000;
  color: #fff;
}
</style>