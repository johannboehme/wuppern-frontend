<template>
    <div class="gameOverview">
        <li v-for="gamename in gamenames" :key="gamename" > 
            {{ gamename }} 
            <button>mitspielen</button>
        </li>
    </div>
</template>

<script>
export default {
    name: "GameOverview",
    props: {
        gamenames: Array,
    }
}
</script>

<style scoped>
    li {
        list-style: none;
        margin: 5px;
    }
    button {
        background: blue;
        color: white;
        border-radius: 3px;
        padding: 5px;
        border: none;
        box-shadow: 0 0 1px 2px rgba(0, 0, 0, 0.2);
    }
</style>