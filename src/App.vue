<template>
  <img v-bind:src="image" class="image">
  <div>Inventory: {{ inventory }}</div>
  <p v-if="inventory > 10">In Stock</p>
  <p v-else-if="inventory <= 10 && inventory > 0">Almost sold out!</p>
  <p v-else>Out of Stock</p>
  <p v-show="inStock">Shown</p>
  <product-display :premium="premium" :inStock="inStock" @addToCart="updateCart"></product-display>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue';
import { print } from './utils/utils';
import ProductDisplay from './components/ProductDisplay.vue';

export default defineComponent({
  name: 'App',
  components: {
    ProductDisplay
  },
  data() {
    return {
      image: 'https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png',
      premium: true,
      inventory: 8,
      inStock: true,
    };
  },
  mounted() {
    print('hello vue3 + typescript!');
  },
  methods: {
    updateCart() {
      this.inventory--;
      this.inventory > 0 ? this.inStock = true : this.inStock = false;
    }
  },
  setup() {
    const title = computed(() => {
      return 'Vue3 Studio Boots';
    });
    return {
      title
    };
  }
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
