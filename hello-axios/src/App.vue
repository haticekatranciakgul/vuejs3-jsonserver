<template>
  <di>
    <h1>Todos</h1>
    <ul>
      <li v-for="todo of todos" :key="todo.id">
        {{ todo.name }}
      </li>
    </ul>
  </di>
</template>

<script>
import axios from "axios";

export default {
  name: "TodoList",
  data() {
    return {
      todos: []
    };
  },
  async created() {
    try {
      const res = await axios.get(`http://localhost:3001/todos`);

      this.todos = res.data;
    } catch (e) {
      console.error(e);
    }
  }
};
</script>

<style scoped>
h1 {
  text-decoration: underline;
}

li {
  color: white;
}
</style>