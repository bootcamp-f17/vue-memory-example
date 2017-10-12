<template>

  <div class="board">
  
    <card></card>

  </div>

</template>

<script>
import card from './card.vue';

export default {
  name: 'board',
  components: { card },
  data: function() {
    return {

    }
  },
  methods: {

  }

}

</script>

<style>

.board {
  border: 1px solid #ccc;
}

</style>