<template>
  <div class="todo-item">
    <app-checkbox :isDone="todo.isDone" @toggleDone="$emit('toggleDone')"></app-checkbox>
    <p>{{ todo.name }}</p>
    <div class="img__wrap" @click="$emit('delete')">
      <img src="https://cdn0.iconfinder.com/data/icons/slim-square-icons-basics/100/basics-22-256.png" title="Удалить">
    </div>
    <div class="img__wrap" @click="$emit('edit')">
      <img src="https://cdn3.iconfinder.com/data/icons/google-material-design-icons/48/ic_mode_edit_48px-256.png" title="Редактировать">
    </div>
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
  flex-wrap: wrap;
  align-items: center;
  
}
.todo-item p {
  margin-right: 15px;
}

.img__wrap {
  border: 1px solid rgba(0,0,0,0.3);
  border-radius: 50%;
  padding: 5px;
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 5px;
}

.img__wrap:hover{
  opacity: 0.6;
  cursor: pointer;
}

img {
   width:20px;
}
</style>