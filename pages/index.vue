<template>
  <div>
    <div class="container">
      <GameModeSection @setGameMode="setGameMode" />
    </div>
  </div>
</template>

<script>
import GameModeSection from "../components/GameModeSection.vue";
export default {
  components: {
    GameModeSection,
  },
  data() {
    return {
      gameMode: null,
    };
  },
  methods: {
    setGameMode(mode) {
      this.gameMode = mode;
    },
  },
};
</script>

<style></style>
