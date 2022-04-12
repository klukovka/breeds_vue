<template>
  <div class="breeds-list">
    <p>Список пород</p>
    <div v-if="loading"><p>Loading...</p></div>
    <breed-item
      v-else
      :breed="breed"
      v-for="breed in breeds"
      v-bind:key="breed.breed"
    />
  </div>
</template>

<script>
import BreedItem from './BreedItem.vue';
export default {
  components: { BreedItem },
  name: 'breeds-list',
  data() {
    return {
      urlBreeds: 'https://dog.ceo/api/breeds/list/all',
      breeds: [],
      errors: [],
      loading: true,
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
        this.breeds.push({ breed: key, subbreeds: value });
      });

      this.loading = false;
    } catch (error) {
      this.errors.push(error);
    }
  },
};
</script>

<style scoped>
.breeds-list {
  flex: 0 0 50%;
  padding-right: 8px;
}
p {
  color: teal;
  font-size: 24px;
  font-weight: 800;
}
</style>
