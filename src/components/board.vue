<template>

  <div class="board">
  
    <card 
      v-for="(card, index) in deck.cards" 
      v-bind:face=card.face
      v-bind:showing=card.showing
      v-bind:index=index
      v-bind:flippable=card.flippable
      v-bind:flips="flipped.length"
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
      turn: 0,      // turn number
      pairs: 0,     // number of matches made
      flipped: [],  // the cards that are flipped in this turn
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

    noMatchThisTurn: function() {
      this.deck.cards[this.flipped[0]].flippable = true;
      this.deck.cards[this.flipped[0]].showing = false;
      this.deck.cards[this.flipped[1]].flippable = true;
      this.deck.cards[this.flipped[1]].showing = false;
      this.turn++;
      this.flipped = [];

      console.log('in noMatchThisTurn...last line');
    },

    flipCard: function(index) {
      this.deck.cards[index].showing = !this.deck.cards[index].showing;
      this.deck.cards[index].flippable = false;
      this.flipped.push(index);
      if (this.flipped.length == 2) {

        if (
          this.deck.cards[this.flipped[0]].face === 
          this.deck.cards[this.flipped[1]].face) {

            // we have a match!
            this.turn++;
            this.pairs++;
            this.flipped = [];

            // check for win
            if (this.deck.cards.length/2 === this.pairs) {

              // game is won!
              alert('we won!');

            }

        }
        else {

          console.log('not a match, resetting cards');

          // not a match, turn cards back over
          setTimeout(this.noMatchThisTurn(), 5000);

        }

      }
    }
  }

}

</script>

<style>

.board {
  /*border: 1px solid #ccc;*/
}

</style>