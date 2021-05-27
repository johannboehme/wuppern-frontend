<template>
<div class="upper">
    <div v-for="player in players" :key="player" class="spielercontainer">
        <div class="spieler">
            {{player.name}}: {{player.punkte}} <br>
            {{player.aktuell}}/{{player.angesagt}}
        </div>
        <GespielteKarte :playedCards="playedCards" :playerName="player.name" />
    </div>
</div>
</template>

<script>
    import GespielteKarte from "@/components/GespielteKarte";

    export default {
        name: "Spieler",
        components: {
            GespielteKarte,
        },
        props: {
            players: Array,
            playedCards: Array,
        }
    }
</script>

<style scoped>
    .upper {
        width: 100%;
        display: flex;
        justify-content: space-around;
    }
    .spieler {
        border: 3px solid brown;
        padding: 10px;
        width: 100px;
        border-radius: 100px;
        position: relative;
        margin-top: 30px;
        font-size: .8rem;
        
    }
    .spielercontainer {
        margin-bottom: 5px;
        width: 100px;
        height: 400px;
        position: relative;

    }
</style>