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
      <p @click="deleteTodo(todo.id)">削除</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data: function() {
    return {
      latestId: 0,
      todos: [],
      inputText: ""
    };
  },
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
