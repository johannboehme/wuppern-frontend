<template>
  <div class="home">
    <JoinGame />
    <CreateGame v-if="false" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from "@/components/HelloWorld.vue";
import CreateGame from "@/components/CreateGame.vue";
import JoinGame from "@/components/JoinGame.vue"

export default {
  name: "Home",
  components: {
//    HelloWorld,
    CreateGame,
    JoinGame,
  },
};
</script>

