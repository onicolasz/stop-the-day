<template>
  <div class="ranking">
    <h2 class="ranking-title">Ranking</h2>
    <div class="gamemodes">
      <div class="mode">
        <h3>Normal</h3>
        <div
          class="normal-positions"
          v-for="ranked in ranking"
          :key="ranked.id"
        >
          <h4>{{ ranked.position }}. {{ ranked.name }} {{ ranked.time }}</h4>
        </div>
      </div>
      <div class="mode">
        <h3>Duplo</h3>
        <div
          class="double-positions"
          v-for="ranked in ranking"
          :key="ranked.id"
        >
          <h4>{{ ranked.position }}. {{ ranked.name }} {{ ranked.time }}</h4>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Ranking",
  props: {
    ranking: {
      default: Array,
    },
  },
};
</script>

<style lang="scss" scoped>
.ranking {
  position: absolute;
  right: 100px;
  font-size: 15px;
  background-color: white;

  .gamemodes {
    display: flex;
    flex-direction: row;
  }

  .ranking-title {
    margin: 10px;
    text-align: center;
  }
  .ranking-positions {
    margin: 2px;
  }

  h3 {
    margin-bottom: 20px;
  }

  .mode {
    margin: 20px;
  }
}

@media (max-width: 1200px) {
  .ranking {
    right: 0;
    position: relative;
    text-align: center;
    font-size: 20px;
    margin-top: 20px;
  }
}

@media (max-width: 750px) {
  .ranking {
    right: 0;
    position: relative;
    text-align: center;
    font-size: 15px;
    margin-top: 20px;
  }
}

@media (max-width: 300px) {
  .ranking {
    right: 0;
    position: relative;
    text-align: center;
    font-size: 10px;
    margin-top: 0;
  }
}
</style>
