<template>
  <v-app>
    <v-content>
      <div class="title-section">
        <h1 class="title">Cards</h1>
        <div class="main-buttons">
          <v-btn color="primary" v-on:click="shuffle()">Shuffle</v-btn>
        </div>
      </div>
      <deck ref="deck"/>
    </v-content>
  </v-app>
</template>

<script>
import { Deck } from './components/cards';

export default {
  name: 'App',
  components: {
    Deck
  },
  methods: {
    shuffle: function() {
      this.$refs.deck.shuffle();
    },
  },
};
</script>

<style>
html, body, #app {
  height: 100%;
  background: ghostwhite;
}
.title-section {
  font-family: Roboto Slab, sans-serif;
  text-align: center;
  margin-top: 30px;
}

.main-buttons {
  display: block;
  margin: 0 auto;
  padding-bottom: 30px;
  text-align: center;
  margin-bottom: 0px;
}
.main-buttons > button {
  margin-left: 10px;
}
</style>