<template>
    <div class="spielfeld">
        <h3>Runde {{ runde.aktuell }} / {{ runde.maximal }}</h3>
        <Spieler :players="players" :playedCards="playedCards" />
        <Handkarten :ownCards="ownCards" :playcard="playcard($event)" />
    </div> 
</template>

<script>
    import Handkarten from "@/components/Handkarten.vue";
    import Spieler from "@/components/Spieler.vue";
    import io from "socket.io-client";
    import { mapActions } from 'vuex';


export default {
    name: "Spielfeld",
    components: {
        Handkarten,
        Spieler,
    },
    data() {
        return {
            socket: {},
            username: '',
            room: "raum1",
            runde: {},
            players: [
                {
                    name: "Manu",
                    punkte: 21,
                    angesagt: 2,
                    aktuell: 0
                }, 
                {
                    name: "Laura",
                    punkte: 33,
                    angesagt: 0,
                    aktuell: 0
                },
                {
                    name: "Jan",
                    punkte: 12,
                    angesagt: 2,
                    aktuell: 0
                },
                { 
                    name: "das ist die html seite bro, der server läd nicht",
                    punkte: 14,
                    angesagt: 1,
                    aktuell: 0
                }
            ],
            ownCards: [
                {zahl: "7", farbe: "♠"},
                {zahl: "10", farbe: "♣"},
                {zahl: "A", farbe: "♦"},
                {zahl: "D", farbe: "♥"},
            ],
            playedCards: [
                { player: "Manu", zahl: "9", farbe: "♣"},
                { player: "Laura", zahl: "7", farbe: "♣"},
                //{ player: "Jan", zahl: "D", farbe: "♦"},
                //{ player: "Simon", zahl: "10", farbe: "♣"}
            ]
        }
    },
    created() {
        this.socket = io("http://localhost:3000")
    },
    mounted() {
        if(localStorage.username){
            this.name = localStorage.username;
        }
        this.socket.emit('joinRoom', this.name, this.room)
        this.socket.on("gamestate", data => {
            if(data){
                let gamestate = JSON.parse(data);
                this.setGamestate(gamestate)
                console.log(this.$store.state.gamestate)
                this.players = gamestate.players;
                console.log(this.players)
                console.log(gamestate.players)
                this.playedCards = gamestate.playedCards;
                this.runde = gamestate.runde;
                this.ownCards = gamestate.handkarten
            }
        })
    },
    methods: {
        playcard(name, card){
            console.log(this.playedCards, name, card)
            //this.playedCards.push({player: name, zahl: card.zahl, farbe: card.farbe})
        },
        ...mapActions([
            'nameDerAction',
        ]),
    }
}
</script>

<style>
* {
    box-sizing: border-box;
}
</style>

<style scoped>
    .spielfeld {
    box-sizing: border-box;
    border: 2px solid black;
    min-width: 600px;
    max-width: 1000px;
    height: 600px;
    margin: auto;
    position: relative;
    }
</style>