<template>
  <div>
    <div class="buttons">
      <my-button @press="onAddPress">Add</my-button>
      <my-button @press="onRemovePress">Remove</my-button>
      <my-button @press="onMixPress">Mix</my-button>
    </div>
    <ul>
      <breed-image :url="dog" v-for="dog in dogs" v-bind:key="dog" />
      <div v-if="loading"><p>Loading...</p></div>
    </ul>
  </div>
</template>

<script>
import BreedImage from './BreedImage.vue';
import MyButton from './MyButton.vue';
export default {
  name: 'breeds-image-list',
  components: { MyButton, BreedImage },
  data() {
    return {
      dogs: [],
      loading: false,
      urlRandom: 'https://dog.ceo/api/breeds/image/random',
    };
  },
  methods: {
    async onAddPress() {
      this.loading = true;
      const response = await fetch(this.urlRandom);
      const result = await response.json();
      this.dogs.push(result.message);
      this.loading = false;
    },
    onRemovePress() {
      const index = Math.floor(Math.random() * this.dogs.length);
      this.dogs.splice(index, 1);
    },
    onMixPress() {
      for (var i = this.dogs.length - 1; i > 0; i--) {
        var j = Math.floor(Math.random() * (i + 1));
        var temp = this.dogs[i];
        this.dogs[i] = this.dogs[j];
        this.dogs[j] = temp;
      }
    },
  },
};
</script>

<style>
.buttons {
  padding-top: 16px;
  justify-content: space-around;
  display: flex;
}
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
</style>
