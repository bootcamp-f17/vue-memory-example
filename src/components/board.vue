<template>

  <div class="board">
  
    <card 
      v-for="(card, index) in deck.cards" 
      v-bind:face=card.face
      v-bind:showing=card.showing
      v-bind:index=index
      v-bind:flippable=card.flippable
      v-bind:flips="flips"
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
      turn: 0,
      flips: 0,
      pairs: 0,
      deck: {
        cards: [
          {
            face: 'A',
            showing: false,
            flippable: true
          },
          {
            face: 'B',
            showing: false,
            flippable: true
          },
          {
            face: 'B',
            showing: false,
            flippable: true
          },
          {
            face: 'A',
            showing: false,
            flippable: true
          }
        ]
      }
    }
  },
  methods: {
    flipCard: function(index) {
      this.deck.cards[index].showing = !this.deck.cards[index].showing;
      this.deck.cards[index].flippable = false;
      this.flips++;
    }
  }

}

</script>

<style>

.board {
  /*border: 1px solid #ccc;*/
}

</style>