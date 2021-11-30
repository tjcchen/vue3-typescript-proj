<template>
  <div>
    <form action="#" method="post" class="review-form" @submit.prevent="onSubmit">
      <h3>Leave a reivew</h3>
      <label for="name">name: </label>
      <input id="name" v-model="name" @change="printName"/>
      <br/>
      <label for="review">Review:</label>
      <textarea id="review" v-model="review"></textarea>
      <br/>
      <label for="rating">Rating:</label>
      <select id="rating" v-model.number="rating">
        <option>5</option>
        <option>4</option>
        <option>3</option>
        <option>2</option>
        <option>1</option>
      </select>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      name: 'Andy',
      review: '',
      rating: null,
    };
  },
  methods: {
    printName() {
      console.log(this.name);
    },
    onSubmit() {
      let productReview = {
        name: this.name,
        review: this.review,
        rating: this.rating,
      };
      this.$emit('review-submitted', productReview);
      this.name = '';
      this.review = '';
      this.rating = null;
    }
  }
});
</script>

<style>

</style>