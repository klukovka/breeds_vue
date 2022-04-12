<template>
  <input type="text" class="input" :value="value" @input="updateInput" />
</template>

<script>
export default {
  name: 'my-input',
  props: {
    value: [String, Number],
  },
  methods: {
    updateInput(event) {
      this.$emit('update:value', event.target.value);
    },
  },
};
</script>

<style scoped>
.input {
  width: 100%;
  padding: 12px;
  border: 1px solid teal;
  font-size: 24px;
}
</style>
