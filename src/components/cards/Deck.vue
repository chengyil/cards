<template>
    <transition-group class="deck" tag="div" name="shuffleMedium">
      <card v-for="card in cards" v-bind:card="card" v-bind:key="card.id" />
    </transition-group>
</template>

<script> 
    import { Card } from '@/components/cards';
    const names = ['A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K'];
    const suits = ['♥','♦','♠','♣'];
    export default {
        components: {
            Card
        },
        created: function() {
            this.shuffle()
        },
        data: function() {
            return {
                cards: [],
            };
        },
        methods: {
            initialize: function() {
                this.cards = [];
                suits.forEach(suit => {
                    names.forEach(name => {
                        let id = this.cards.length;
                        let card = {
                            id: id,
                            suit: suit,
                            name: name,
                            selected: false
                        };
                        this.cards.push(card);
                    });
                });
                return this.cards;
            },
            shuffle: function() {
                this.initialize();

                let counter = this.cards.length;

                while(counter > 0) {
                    let index = Math.floor(Math.random() * counter);
                    counter -= 1;
                    let temp = this.cards[counter];
                    this.$set(this.cards, counter, this.cards[index]);
                    this.$set(this.cards, counter, this.cards[index]);
                    this.$set(this.cards, index, temp);
                }

                return this.cards;
            }
        }
    }
</script>

<style scoped>

.deck {
    margin-left: 30px;
}

.shuffleMedium-move {
    transition: transform 1s;
}

</style>