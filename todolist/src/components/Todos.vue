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
    <footer class="footer">
      <span class="todo-count">
        <strong class="">{{ remaining }}</strong>
        Taches a faire
      </span>
      <ul class="filters">
        <li>
          <a
            href="#"
            :class="{ selected: filter === 'all' }"
            @click.prevent="filter = 'all'"
            >Toutes</a
          >
        </li>
        <li>
          <a
            href="#"
            :class="{ selected: filter === 'todo' }"
            @click.prevent="filter = 'todo'"
            >A faire</a
          >
        </li>
        <li>
          <a
            href="#"
            :class="{ selected: filter === 'done' }"
            @click.prevent="filter = 'done'"
            >Faites</a
          >
        </li>
      </ul>
    </footer>
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
      filter: "all",
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
  computed: {
    remaining: function() {
      return this.todos.filter((todo) => !todo.completed).length;
    },
  },
};
</script>

<style src="@/styles/todos.css"></style>
