<template>
  <p>Привет, {{ value.length == 0 ? 'незнакомец' : value }}</p>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
p {
  color: teal;
  font-size: 24px;
  font-weight: 800;
}
</style>
