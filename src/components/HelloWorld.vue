<template>
  <div class="container">
    <input type="text" v-model="newTodo" placeholder="new todo" />
    <button @click="addTodo">Add new todo</button>
    <NewTodo :todos="todos" />
  </div>
</template>

<script>
import { ref } from "vue";
import NewTodo from "@/components/NewTodo";
export default {
  components: {
    NewTodo,
  },
  setup() {
    const newTodo = ref("");
    const todos = ref([]);

    const addTodo = () => {
      if (newTodo.value !== "") {
        todos.value.push({
          content: newTodo.value,
          done: false,
        });
      }
      newTodo.value = "";
    };
    return {
      newTodo,
      addTodo,
      todos,
    };
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  width: 50%;
  margin: 0 auto;
}

input {
  margin-bottom: 1rem;
  font-size: 1.5rem;
  padding: 0.5rem;
  outline: none;
  text-align: center;
  border-color: #374e63;
  cursor: pointer;
  caret-color: #374e63;
}

button {
  padding: 0.5rem;
  font-size: 1.4rem;
}
</style>