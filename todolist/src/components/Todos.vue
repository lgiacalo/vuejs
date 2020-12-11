<template>
  <section class="todoapp">
    <header class="header">
      <h1>Todos</h1>
      <input
        type="text"
        class="new-todo"
        placeholder="Ajouter une tache"
        v-model="newTodo"
        @keyup.enter="addTodo"
      />
    </header>
    <div class="main">
      <ul class="todo-list">
        <li
          class="todo"
          v-for="todo in todos"
          :class="{ completed: todo.completed }"
          :key="todo.name"
        >
          <div class="view">
            <input type="checkbox" v-model="todo.completed" class="toggle" />
            <label>{{ todo.name }}</label>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "Todos",
  data: function() {
    return {
      todos: [
        {
          name: "Tache de test",
          completed: false,
        },
      ],
      newTodo: "",
    };
  },
  methods: {
    addTodo: function() {
      this.todos.push({
        completed: false,
        name: this.newTodo,
      });
      this.newTodo = "";
    },
  },
};
</script>

<style src="@/styles/todos.css"></style>
