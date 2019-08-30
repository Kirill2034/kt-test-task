<template>
  <div class="modal">
    <div class="modal__overlay">
      <div class="modal__content">
        <div class="modal__title"></div>
        <div class="modal__form">
          <input class="input" placeholder="Редактирование" v-model="name" />
          <button @click="$emit('onEdit', name)">Редактировать</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object
    }
  },
  data() {
    return {
      name: ""
    };
  },
  created() {
    this.name = this.todo.name;
  }
};
</script>

<style scoped>
.modal {
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
}
.modal__overlay {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.3);
}

.modal__content {
  padding: 20px;
  background-color: #fff;
  border-radius: 6px;
  width: 600px;
  animation: zoomIn 0.2s ease;
}

@keyframes zoomIn {
  0% {
    opacity: 0;
    transform: scale(0.7);
  }

  100% {
    opacity: 1;
    transform: scale(1);
  }
}

.modal__title {
  margin-bottom: 20px;
  font-size: 16px;
  font-weight: 600;
}

.modal__form {
  display: flex;
  flex-direction: column;
}
.input {
  margin-bottom: 30px;
  padding: 10px;
  border-radius: 4px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  outline: none;
}
button {
  padding: 10px 20px;
  font-size: 20px;
  border-radius: 4px;
  border: none;
  outline: none;
  cursor: pointer;
  transition: background-color 0.02s ease;
}
</style>