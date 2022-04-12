<template>
  <div class="app">
    <hello-stranger v-model:value="stranger" />
    <my-input v-model:value="stranger" />
    <div class="block">
      <breeds-list />
      <div class="inner-block">
        <breed-random />
        <breed-image-list />
      </div>
    </div>
  </div>
</template>

<script>
import HelloStranger from './components/HelloStranger.vue';
import MyInput from './components/MyInput.vue';
import BreedsList from './components/BreedsList.vue';
import BreedRandom from './components/BreedRandom.vue';
import BreedImageList from './components/BreedImageList.vue';
export default {
  components: {
    HelloStranger,
    MyInput,
    BreedsList,
    BreedRandom,
    BreedImageList,
  },
  name: 'App',
  data() {
    return {
      stranger: '',
    };
  },
};
</script>

<style>
.app {
  padding: 20px;
  color: rgb(198, 241, 241);
}
.block {
  display: flex;
  word-break: break-all;
}
.inner-block {
  flex: 0 0 50%;
  padding-left: 8px;
}
</style>
