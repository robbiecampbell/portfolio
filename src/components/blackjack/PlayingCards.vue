<template>
  <div>
    <button class="button" @click="stick">
      stick
    </button>
    <button class="button" @click="dealCards(currentPlayer)">
      hit
    </button>

    <div class="columns">
      <div class="column is-half is-offset-one-quarter">
        <div id="playersHand">
          <h1> dealers hand </h1>
          <div v-for="card in dealerCards" :key="card.id" class="card" :class="suitColour[card.suit]">
            <span class="cardSuit cardSuitTop">{{card.suit}}</span>
            <span class="cardValue">{{card.value}}</span>
            <span class="cardSuit cardSuitBottom">{{card.suit}}</span>
          </div>
        </div>
      </div>
    </div>

    <div class="columns">
      <div class="column is-half is-offset-one-quarter">
        <div id="playersHand">
          <h1> players hand </h1>
          <div v-for="card in playerCards" :key="card.id" class="card" :class="suitColour[card.suit]">
            <span class="cardSuit cardSuitTop">{{card.suit}}</span>
            <span class="cardValue">{{card.value}}</span>
            <span class="cardSuit cardSuitBottom">{{card.suit}}</span>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>
  <!-- <div class="deck">
    <div
      v-for="card in deck"
      :key="card.id"
      class="card"
      :class="suitColour[card.suit]">
      <span class="cardSuit cardSuitTop">{{card.suit}}</span>
      <span class="cardValue">{{card.value}}</span>
      <span class="cardSuit cardSuitBottom">{{card.suit}}</span>
    </div>
  </div> -->

<script lang="ts">
import {Vue, Component} from 'vue-property-decorator';

@Component
export default class PlayingCards extends Vue {
  private cardValues: Array[string] = ['A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K'];
  private suits: Array[string] =  ['♥','♦','♠','♣'];
  private deck: any = [];
  private suitColour: any = {
      '♠': 'black',
      '♣': 'black',
      '♦': 'red',
      '♥': 'red',
    };

  private dealerCards: any = [];
  private playerCards: any = [];
  private currentPlayer: any = [];
  private playerList: any = [
    this.playerCards,
    this.dealerCards,
  ];

  private mounted() {
    this.initialiseDeck();
    this.currentPlayer.push(this.playerList[0])
    this.shuffleDeck();
    for (let i = 0; i < 2; i++) {
      this.dealCards(this.playerList)
    }
    if(this.checkHandValue == 21) this.$toast.open('you got 21!')
  }

  private initialiseDeck() {
    let id: number = 1;
    for (let s = 0; s < this.suits.length; s++) {
      for (let r = 0; r < this.cardValues.length; r++ ) {
        const card = {
          id: id,
          value: this.cardValues[r],
          suit: this.suits[s],
        }
        this.deck.push(card);
        id++;
      }
    }
  }

  private shuffleDeck() {
    for (let i = this.deck.length - 1; i > 0; i--) {
      let randomIndex = Math.floor(Math.random() * i);

      let temp = this.deck[i];
      Vue.set(this.deck, i, this.deck[randomIndex]);
      Vue.set(this.deck, randomIndex, temp);
    }
  }

  private dealCards(playerList) {
    console.log("playerList: " + playerList)
    console.log("checkHandValue: " + this.checkHandValue())
    if(this.checkHandValue() < 21) {
      console.log("playerList2: " + playerList)
      for(let j = 0; j < playerList.length; j++) {
        playerList[j].push(this.deck.shift())
        }
        if(this.checkHandValue() > 21) this.$toast.open('You went bust!')
    }
    else if(this.checkHandValue() == 21) this.$toast.open('you got 21!')
    else this.$toast.open('You went bust!')

  }

  private stick() {
    this.currentPlayer[0] = this.playerList[1]
  }

// TODO: deal with ace properly (can be 11 or 1)

  private checkHandValue() {
    let value: number = 0
    for(let i = 0; i < this.currentPlayer[0].length; i++) {
      switch(this.currentPlayer[0][i].value) {
        case 'J':
        case 'Q':
        case 'K':
          value = value + 10
          break;
        case 'A':
          if(value + 11 > 21) value = value + 1
          else value = value + 11
          break;
        default:
          value = value + parseInt(this.currentPlayer[0][i].value)
      }
    }
      return value
    }

  }
</script>

<style>

#playersHand {
  border-style: solid;
  border-width: 1px;
  margin: auto;
}

.deck {
  margin-left: 30px;
  padding-top: 30px;
}

.card {
  width: 75px;
  height: 100px;
  float: left;
  margin-right: 5px;
  margin-bottom: 5px;
  border-radius: 2px;
}

.cardSuit {
  width: 100%;
  display: block;
}

.cardSuitTop {
  text-align: left;
  padding-left: 5px;
}

.cardSuitBottom {
  position: absolute;
  bottom: 0px;
  text-align: left;
  transform: rotate(180deg);
  padding-left: 5px;
}

.cardValue {
  position: absolute;
  top: 38%;
  text-align: center;
}

.red {
  color: #FF0000;
}

.black {
  color: #000;
}
</style>
