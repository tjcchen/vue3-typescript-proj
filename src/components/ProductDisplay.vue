<template>
  <div>
    <h3>shipping: {{ shipping }}</h3>
    <p @mouseover="onMouseOver(1)">{{ combinedName }}</p>
    <p @mouseover="onMouseOver(2)">I love {{ product }}</p>
    <p @mouseover="onMouseOver(3)">{{ getValue() }}</p>
    <h3>{{ firstName + ' ' + lastName }}</h3>s
    <h3 :style="styles">{{ clicked ? true : false }}</h3>
    <button :disabled="!inStock" :class="{ disabledButton: !inStock }" @click="addToCart">Add to Cart</button>
    <ol>
      <li
        v-for="variant in variants"
        :key="variant.id"
        :style="{ backgroundColor: variant.color }"
        :class="{ active: activeClass }"
        class="color-circle"
      ></li>
    </ol>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    premium: {
      type: Boolean,
      required: true,
      default: false
    },
    inStock: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      brand: 'Vue3 Studio',
      product: 'Socks',
      firstName: 'Andy',
      lastName: 'Chen',
      clicked: true,
      details: ['50% cotton', '30% wool', '20% polyester'],
      variants: [
        { id: 1234, color: 'green' },
        { id: 5678, color: 'blue' }
      ],
      cart: 0,
      styles: {
        color: 'red',
        fontSize: '14px'
      },
      activeClass: true,
      isShown: true,
    };
  },
  methods: {
    getValue(): string {
      return 'vue3 + typescript';
    },
    addToCart(): void {
      this.$emit('addToCart');
    },
    onMouseOver(number: number) {
      console.log(number);
    }
  },
  computed: {
    combinedName(): string {
      return this.brand + ' ' + this.product;
    },
    shipping() {
      if (this.premium) {
        return 'Free';
      }
      return 2.99;
    }
  },
});
</script>

<style>
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
.disabledButton {
  background: #d8d8d8;
  cursor: not-allowed;
}
</style>