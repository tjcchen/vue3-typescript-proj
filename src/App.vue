<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <p>{{ product }}</p>
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
      product: 'Socks'
    };
  },
  mounted() {
    print('hello vue3 + typescript!');
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
</style>
