<template>
  <div class="todo-item">
    <app-checkbox :isDone="todo.isDone" @toggleDone="$emit('toggleDone')"></app-checkbox>
    <p>{{ todo.name }}</p>
    <app-button color="red" @click="$emit('delete')" text="Удалить"></app-button>
    <app-button color="pure" @click="$emit('edit')" text="Редактировать"></app-button>
  </div>
</template>

<script>
import AppButton from "./AppButton.vue";
import AppCheckbox from "./AppCheckbox.vue";

export default {
  props: {
    todo: {
      type: Object
    }
  },
  components: {
    AppButton,
    AppCheckbox
  }
};
</script>

<style scoped>
.todo-item {
  padding: 5px;
  display: flex;
  align-items: center;
}
.todo-item p {
  margin-right: 15px;
}
</style>