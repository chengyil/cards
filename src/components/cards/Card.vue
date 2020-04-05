<template>
    <v-card class="card white" v-bind:class="selected && suitColor()" v-on:click="select()">
        <div v-if="selected">
            <span class="card__suit card__suit--top">{{ card.suit }}</span>
            <span class="card__number">{{ card.name }}</span>
            <span class="card__suit card__suit--bottom">{{ card.suit }}</span>
        </div>
        <div v-if="!selected">
            <v-img
            max-height max-width
                src="https://i.pinimg.com/originals/10/80/a4/1080a4bd1a33cec92019fab5efb3995d.png"
          ></v-img>

        </div>
    </v-card>
</template>

<script>
    export default {
        props: {
            card: {
                type: Object
            }
        },
        methods: {
            suitColor: function() {
                if(this.card.suit === '♠' || this.card.suit ===  '♣') {
                    return 'black--text';
                } else {
                    return 'red--text';
                }
            },
            select: function() {
                this.card.selected = true;
            }
        },
        computed: {
            selected: function() {
                return this.card.selected;
            }
        },
        watch: {
            "card.selected": function () {
                console.log(this.card);

            }
        }
    }
</script>

<style scoped>
.card {
    background-color: white;
    width: 75px;
    height: 100px;
    float: left;
    margin-right: 5px;
    margin-bottom: 5px;
    border-radius: 2px;
    max-width: 100%;
}

.card__suit {
    width: 100%;
    display: block;
}

.card__suit--top {
    text-align: left;
    padding-left: 5px;
}

.card__suit--bottom {
    position: absolute;
    bottom: 0px;
    text-align: left;
    transform: rotate(180deg);
    right: 5px;
}

.card__number {
    position: absolute;
    top: 38%;
    text-align: center;
    width: 100%;

}
</style>