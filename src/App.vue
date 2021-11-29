<template>
  <img v-bind:src="image" class="image">
  <product-display :premium="premium"></product-display>
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
    };
  },
  mounted() {
    print('hello vue3 + typescript!');
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
