<template>
  <div class="gamemode-container">
    <div class="mode-title">
      <h1>Escolha o modo de jogo</h1>
    </div>
    <div class="gamemode-buttons">
      <div class="gamemode" @click="setGameMode('normal')">
        <h1>1 Letras</h1>
      </div>
      <div class="gamemode" @click="setGameMode('double')">
        <h1>2 Letras</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "GameModeSection",
  data() {
    return {};
  },
  methods: {
    setGameMode(mode) {
      this.$emit("setGameMode", mode);
    },
  },
};
</script>

<style lang="scss" scoped>
.gamemode-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: rgb(1, 40, 112);
  height: 100%;
}

.gamemode-buttons {
  display: flex;
  flex-direction: row;
}

.mode-title {
  margin: 50px;
}

.gamemode {
  padding: 8px 16px;
  border: 2px solid rgb(1, 40, 112);
  border-radius: 4px;
  margin: 10px;
}

@media (max-width: 490px) {
  .mode-title {
    text-align: center;
  }
}

@media (max-width: 340px) {
  .gamemode-buttons {
    display: flex;
    flex-direction: column;
  }
}
</style>
