<template>
  <div>
    <input type="checkbox" :checked="isDone" @click="$emit('toggleDone')" />
  </div>
</template>

<script>
export default {
  props: {
    isDone: {
      type: Boolean
    }
  }
};
</script>

<style scoped>
input {
  width: 20px;
  height: 20px;
  margin-right: 20px;
}
</style>