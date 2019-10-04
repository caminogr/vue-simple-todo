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
      <p>message: {{ todo.title }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data: function() {
    return {
      todos: [],
      inputText: ""
    };
  },
  methods: {
    submit: function(text) {
      const id = this.todos.length + 1;
      this.todos.push({ id, title: text });
      this.inputText = "";
    }
  },
  components: {}
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
