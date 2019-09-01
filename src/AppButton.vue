<template>
  <div>
    <div :class="['app-button', color]" @click="$emit('click')">{{ text }}</div>
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: ""
    },
    color: {
      type: String,
      default: ""
    }
  }
};
</script>

<style scoped>
.app-button {
  background-color: rgb(134, 184, 167);
  padding: 6px;
  color: #fff;
  border-radius: 5px;
  cursor: pointer;
  border: 1px solid black;
  margin-left: 10px;
}
.app-button:active {
  background-color: rgb(82, 82, 82);
}
.app-button.red {
  background-color: rgb(226, 113, 113);
}
.app-button.grey {
  background-color: rgb(104, 104, 104);
}
.app-button.pure {
  background-color: rgb(120, 67, 160);
}
</style>