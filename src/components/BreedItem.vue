<template>
  <div class="breed-item">
    <div class="breed-name">Порода: {{ breed.breed }}</div>
    <div class="subbreed-list" v-if="breed.subbreeds.length != 0">
      <div class="subbreed-title">Подпороды:</div>
      <subbreed-item
        :subbreed="subbreed"
        v-for="subbreed in breed.subbreeds"
        v-bind:key="subbreed"
      />
    </div>
  </div>
</template>

<script>
import SubbreedItem from './SubbreedItem.vue';
export default {
  components: { SubbreedItem },
  name: 'breed-item',
  props: {
    breed: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style>
.breed-item {
  padding: 8px;
  border: 2px solid teal;
  margin-top: 8px;
  display: flex;
  flex-direction: column;
  align-items: baseline;
  overflow-wrap: break-word;
}
.breed-name {
  color: teal;
  font-size: 18px;
  font-weight: 700;
  padding: 8px;
}
.subbreed-title {
  color: rgb(0, 37, 37);
  font-size: 16px;
  font-weight: 600;
}
.subbreed-list {
  flex-direction: row;
  display: inline-flex;
  align-items: center;
  overflow-wrap: break-word;
  flex-wrap: wrap;
  padding: 8px;
}
</style>
