<template>
  <div>
    <input :value="value" @input="OnInput" @keyup.enter="$emit('keyUp')"/>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: ""
    }
  },
  methods: {
    OnInput(event) {
      this.$emit("input", event.target.value);
    }
  }
};
</script>

<style scoped>
input {
  outline: none;
  padding: 5px;
  font-size: 14px;
  width: 300px;
  margin-right: 10px;
  margin-bottom: 15px;
}

@media screen and (max-width: 670px) {
  input {
    width: 100%;
    padding: 0;
    height: 30px;
    margin-right: 10px;
  }
}
</style>