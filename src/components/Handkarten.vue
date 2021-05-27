<template>
    <div class="kartencontainer">
        <div 
        v-for="karte in ownCards" 
        :key="karte" 
        class="karte"
        @click="playCard(username, karte)"
        :class="karte.farbe === '♦'|| karte.farbe === '♥'? 'rot' : 'schwarz'"
        
        >
            <div class="oben"> {{karte.zahl}} <i class="farbe"> {{karte.farbe}} </i></div>
            <div class="mitte"> {{karte.farbe}} </div>
            <div class="unten"> {{karte.zahl}} <i class="farbe"> {{karte.farbe}} </i></div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Handkarten",
    props: {
        ownCards: Array,
    },
    data() {
        return {
            username: "Manu"
        }
    },
    methods: {
        playCard(name, playercard) {
            this.$emit('playcard', name, playercard)
        },
        isred(color) {
            if (color == "♦" || color == "♥"){
                return "{color: red}";
            } else {
                return "{color: purple}";
            }
        }
    }
}
</script>

<style scoped>
    .karte {
        
        border: 3px solid black;
        border-radius: 12.5px;
        width: 100px;
        height: 150px;
        position: relative;
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        transition: 250ms ease;
    }
    .karte:hover,
    .karte:focus {
        transform: translateY(-20px);
    }
    .played {
        margin-top: 5px;
    }
    .played:hover,
    .played:focus {
        transform: none;
        cursor: default;
    }
    .kartencontainer {
        position: absolute;
        bottom: 0;
        width: 100%;
        display: flex;
        justify-content: center;
    }
    .farbe {
        font-size: 1.5rem;
    }
    .oben {
        position: absolute;
        top: 0px;
        left: 0px;
        margin-left: 5px;
    }
    .unten {
        position: absolute;
        bottom: 0px;
        right: 0px;
        margin-right: 5px;
        transform: rotate(180deg)

    }
    .mitte {
        font-size: 4rem;
    }
    .rot {
        color: red;
    }
    .schwarz {
        color: black;
    }
</style>
