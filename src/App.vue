<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <p>{{ product }}</p>
  <p>I love {{ product }}</p>
  <p>{{ getValue() }}</p>
  <h3>{{ firstName + ' ' + lastName }}</h3>
  <h3>{{ clicked ? true : false }}</h3>
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
      clicked: true
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
</style>
