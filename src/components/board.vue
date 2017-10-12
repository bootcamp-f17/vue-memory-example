<template>

  <div class="board">
  
    <card 
      v-for="card in deck.cards" 
      v-bind:face=card.face
      v-bind:showing=card.showing
      v-on:flipCard="flipCard">
    </card>

  </div>

</template>

<script>
import card from './card.vue';

export default {
  name: 'board',
  components: { card },
  data: function() {
    return {
      deck: {
        cards: [
          {
            face: 'A',
            showing: true
          },
          {
            face: 'B',
            showing: false
          },
          {
            face: 'B',
            showing: false
          },
          {
            face: 'A',
            showing: false
          }
        ]
      }
    }
  },
  methods: {
    flipCard: function() {
      alert("Flip card!");
    }
  }

}

</script>

<style>

.board {
  /*border: 1px solid #ccc;*/
}

</style>