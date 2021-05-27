<template>
    <div class="spiel">
        <SetUsername v-if="!loggedIn" :login="login" />
        <Waiting v-if="false" />
        <Spielfeld v-if="loggedIn" />
    </div>
</template>

<script>
import Spielfeld from "@/components/Spielfeld.vue";
import SetUsername from "@/components/SetUsername.vue";
import Waiting from "@/components/Waiting.vue";


export default {
    name: "Spiel",
    data() {
        return {
            login: false,
        }
    },
    components: {
        Spielfeld,
        SetUsername,
        Waiting,
    },
    computed: {
        loggedIn() {
            if (localStorage.username) {
                return true;
            } else {
                return false;
            }
        }
    }
}

</script>