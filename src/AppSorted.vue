<template>
  <div>
    <app-button @click="$emit('sorted')" color="grey" :text="getButtonText"></app-button>
  </div>
</template>

<script>
import AppButton from "./AppButton.vue";

export default {
  props: {
    isAsc: {
      type: Boolean
    }
  },
  components: {
    AppButton
  },
  computed: {
    getButtonText() {
      return "Сортировка по " + (this.isAsc ? "возрастанию" : "убыванию");
    }
  }
};
</script>