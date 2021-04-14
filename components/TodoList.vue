<template>
  <section class="container">
    <v-card-actions>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input :checked="todo.done" @change="toggle(todo)" type="checkbox" />
        <span :class="{ done: todo.done }">{{ todo.text }} </span>
        <v-btn @click="removeTodo(todo)">remove</v-btn>
      </li>
    </ul>
     </v-card-actions>
    <p>
      <input
        :value="todoText"
        @input="todoText = $event.target.value"
        placeholder="newtask"
      />
      <v-btn @click="addTodo">add</v-btn>
    </p>
    <p>
      <input
        :value="searchText"
        @input="searchText = $event.target.value"
        placeholder="Search your todo."
      />
    </p>
   

  </section>
</template>

<script>
import { mapMutations } from "vuex";

export default {
  data() {
    return {
      todoText: "",
      searchText: "",
    };
  },
  computed: {
    todos() {
      if (this.searchText.length > 0) {
        return this.$store.state.todos.list.filter((item) =>
          item.text.toLowerCase().includes(this.searchText.toLowerCase())
        );
      }
      return this.$store.state.todos.list;
    },
  },
  methods: {
    addTodo() {
      this.$store.commit("todos/add", this.todoText);
      this.todoText = "";
    },
    ...mapMutations({
      toggle: "todos/toggle",
    }),
    removeTodo(todo) {
      this.$store.commit("todos/remove", todo);
    },
    
    
  },
};
</script>

<style>

v-btn{
  width: 5px;
  height: 5px;
}
</style>