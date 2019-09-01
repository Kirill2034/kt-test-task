<template>
  <div class="todo-list">
    <todo-item
      v-for="(todo) in list"
      :key="todo.createdAt"
      :todo="todo"
      @toggleDone="$emit('toggleDone', todo.createdAt)"
      @delete="$emit('delete', todo)"
      @edit="$emit('edit', todo)"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  props: {
    list: {
      type: Array
    }
  },
  components: {
    TodoItem
  }
};
</script>

<style scoped>
.todo-list {
  font-size: 18px;
  font-family: 'Chilanka', cursive;
}
</style>