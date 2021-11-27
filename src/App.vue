<template>
  <img :alt="alt" v-bind:src="image" class="image">
  <p @mouseover="onMouseOver(1)">{{ product }}</p>
  <p @mouseover="onMouseOver(2)">I love {{ product }}</p>
  <p @mouseover="onMouseOver(3)">{{ getValue() }}</p>
  <h3>{{ firstName + ' ' + lastName }}</h3>
  <h3 :style="styles">{{ clicked ? true : false }}</h3>
  <p v-if="inventory > 10">In Stock</p>
  <p v-else-if="inventory <= 10 && inventory > 0">Almost sold out!</p>
  <p v-else>Out of Stock</p>
  <p v-show="inStock">Shown</p>
  <div>Cart: {{ cart }}</div>
  <button @click="addToCart">Click Me!</button>
  <!-- ul>
    <li v-for="(detail, index) in details" :key="index">
      {{ detail }}
    </li>
  </ul -->
  <ol>
    <li
      v-for="variant in variants"
      :key="variant.id"
      :style="{ backgroundColor: variant.color }"
      class="color-circle"
    ></li>
  </ol>
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
      details: ['50% cotton', '30% wool', '20% polyester'],
      variants: [
        { id: 1234, color: 'green' },
        { id: 5678, color: 'blue' }
      ],
      cart: 0,
      styles: {
        color: 'red',
        fontSize: '14px'
      }
    };
  },
  mounted() {
    print('hello vue3 + typescript!');
  },
  methods: {
    getValue() {
      return 'vue3 + typescript';
    },
    addToCart() {
      this.cart++;
    },
    onMouseOver(number: number) {
      console.log(number);
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
ol, ul, li {
  list-style-type: none;
}
.color-circle {
  width: 50px;
  height: 50px;
  margin-top: 8px;
  border: 1px solid #d8d8d8;
  border-radius: 50%;
}
</style>
