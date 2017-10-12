<template>

  <div 
    class="card" 
    v-bind:class="{ 'back': !showing }" v-on:click="flipCard">{{ face }}
  </div>

</template>

<script>

export default {
  name: 'card',
  props: [ 'face', 'showing', 'index', 'flippable', 'flips'],
  data: function() {
    return {
    }
  },
  methods: {
    flipCard: function() {
      if (this.flippable && this.flips < 2) {
        this.$emit('flipCard', this.index);
      }
    }
  }


}

</script>

<style>

.card {
  height: 50px;
  width: 50px;
  border: 1px solid #ccc;
  display: inline-block;
  margin: 5px;
  color: #000;
}

.back {
  background-color: #000;
}

</style>