<template>

  <div 
    class="card" 
    v-bind:class="{ 'back': showing }" v-on:click="flipCard">{{ face }}
  </div>

</template>

<script>

export default {
  name: 'card',
  props: [ 'face', 'showing'],
  data: function() {
    return {
    }
  },
  methods: {
    flipCard: function() {
      this.$emit('flipCard');
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
}

.back {
  background-color: #ccc;
}

</style>