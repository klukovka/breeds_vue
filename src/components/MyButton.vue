<template>
  <button class="btn" @click="buttonClickHandler"><slot></slot></button>
</template>

<script>
export default {
  name: 'my-button',
  methods: {
    buttonClickHandler() {
      this.$emit('press');
    },
  },
};
</script>

<style scoped>
.btn {
  padding: 8px 16px;
  background: none;
  border: 1px solid teal;
  color: teal;
}
</style>
