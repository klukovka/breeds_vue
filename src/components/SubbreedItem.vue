<template>
  <div class="subbreed-item">
    {{ subbreed }}
  </div>
</template>

<script>
export default {
  name: 'subbreed-item',
  props: {
    subbreed: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scope>
.subbreed-item {
  padding-left: 8px;
  color: red;
  font-size: 16px;
  font-weight: 400;
}
</style>
