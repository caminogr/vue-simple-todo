<template>
  <div id="app">
    Input your todo:
    <input
      type="text"
      class="todo-input"
      v-model="inputText"
      @keyup.enter="submit(inputText)"
    />
    <div v-for="todo in todos" :key="todo.id">
      <Card :todo="todo" :deleteTodo="deleteTodo" />
    </div>
  </div>
</template>

<script>
import Card from "./components/Card";

export default {
  name: "app",
  data: function() {
    return {
      latestId: 0,
      todos: [],
      inputText: ""
      //      isEdit: false
    };
  },
  components: { Card },
  methods: {
    submit: function(text) {
      const id = this.latestId + 1;
      this.todos.push({ id, title: text });
      this.inputText = "";
      this.latestId += 1;
    },
    deleteTodo: function(id) {
      if (window.confirm("本当に削除しますか")) {
        this.todos.splice(this.todos.findIndex(todo => todo.id === id), 1);
      }
    }
  }
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
