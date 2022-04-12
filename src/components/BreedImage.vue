<template>
  <li>
    <div class="image-container">
      <img :src="url" />
      <div class="breed-name">{{ breedName }}</div>
    </div>
  </li>
</template>

<script>
export default {
  name: 'breed-image',
  props: {
    url: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      breedName: '',
    };
  },
  mounted() {
    this.breedName = this.url.replace('https://images.dog.ceo/breeds/', '');
    this.breedName = this.breedName.slice(0, this.breedName.indexOf('/'));
  },
};
</script>

<style scoped>
li {
  margin-top: 12px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1);
  border: 2px solid teal;
}

.image-container {
  width: 100%;
  padding: 10px;
  display: flex;
}

.image-container > img {
  width: 80px;
  height: 80px;
  margin-right: 12px;
  border-radius: 4px;
}
</style>
