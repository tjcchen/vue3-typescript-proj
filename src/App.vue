<template>
  <img :alt="alt" v-bind:src="image" class="image">
  <p>{{ product }}</p>
  <p>I love {{ product }}</p>
  <p>{{ getValue() }}</p>
  <h3>{{ firstName + ' ' + lastName }}</h3>
  <h3>{{ clicked ? true : false }}</h3>
  <p v-if="inventory > 10">In Stock</p>
  <p v-else-if="inventory <= 10 && inventory > 0">Almost sold out!</p>
  <p v-else>Out of Stock</p>
  <p v-show="inStock">Shown</p>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { print } from './utils/utils';

export default defineComponent({
  name: 'App',
  components: {
  },
  data() {
    return {
      product: 'Boots',
      firstName: 'Andy',
      lastName: 'Chen',
      clicked: true,
      alt: 'Google Logo',
      inStock: false,
      inventory: 8,
      image: 'https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png',
    };
  },
  mounted() {
    print('hello vue3 + typescript!');
  },
  methods: {
    getValue() {
      return 'vue3 + typescript';
    }
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.image {
  width: 200px;
  height: 80px;
  object-fit: contain;
}
</style>
