<template>
  <div>
    <p :hidden="isEdit">{{ todo.title }}</p>
    <input v-model="todo.title" :hidden="!isEdit" />
    <p @click="deleteTodo(todo.id)">削除</p>
  </div>
</template>

<script lang="ts">
export default {
  props: ["todo", "delteTodo"],
  data: function() {
    return {
      isEdit: false
    };
  }
};
</script>

<style lang="stylus" scoped></style>
