<template>
  <div class="breed-random">
    <my-button @press="onRandomPress">Random</my-button>
    <breed-item v-if="selectedBreed != null" :breed="selectedBreed" />
  </div>
</template>

<script>
import BreedItem from './BreedItem.vue';
import MyButton from './MyButton.vue';
export default {
  name: 'breed-random',
  components: { MyButton, BreedItem },
  data() {
    return {
      urlBreeds: 'https://dog.ceo/api/breeds/list/all',
      breeds: [],
      errors: [],
      loading: true,
      selectedBreed: null,
    };
  },
  async mounted() {
    try {
      this.loading = true;
      const response = await fetch(this.urlBreeds);
      const result = await response.json();
      let newArray = Object.entries(result.message);
      let map = new Map(newArray);

      map.forEach((value, key) => {
        if (value.length != 0)
          this.breeds.push({ breed: key, subbreeds: value });
      });

      this.loading = false;
    } catch (error) {
      this.errors.push(error);
    }
  },
  methods: {
    onRandomPress() {
      const index = Math.floor(Math.random() * this.breeds.length);
      this.selectedBreed = this.breeds[index];
    },
  },
};
</script>

<style scoped>
.breed-random {
  padding: 16px;
  margin-top: 24px;
  border: 2px solid teal;
}
</style>
