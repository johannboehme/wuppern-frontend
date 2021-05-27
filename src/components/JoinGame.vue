<template>
    <div class="joinGame">
        <GameOverview :gamenames="gamenames" />
    </div>
</template>

<script>
import GameOverview from "@/components/GameOverview.vue"

export default {
    name: "joinGame",
    components: {
        GameOverview,
    },
    data() {
        return {
            gamenames: ["test1", "test2"],
        }
    }
}
</script>