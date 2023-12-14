<template>
  <div class="columns-container">
    <div class="column-card" v-for="column in columns" :key="column.id">
      <div class="column-header">
        <span class="column-title">{{ column.title }}</span>
        <span class="column-letter">{{ column.letter }}</span>
      </div>
      <input type="text" v-model="answers[column.id]" />
    </div>
    <button class="btn-finish" @click="finishGame">Finalizar</button>
  </div>
</template>

<script>
export default {
  name: "GameTable",
  props: {
    columns: {
      default: Array,
    },
  },
  data() {
    return {
      answers: [],
    };
  },
  methods: {
    finishGame() {
      this.$emit("finishGame", this.answers);
    },
  },
  mounted() {
    this.answers = Object.fromEntries(
      this.columns.map((column) => [column.id, ""])
    );
  },
};
</script>

<style lang="scss" scoped>
.columns-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}

.column-card {
  display: flex;
  flex-direction: column;
  flex: 1 0 calc(33% - 40px);
  background-color: white;
  margin: 20px;
  border: 2px solid black;
  padding: 8px;
  border-radius: 5px;
  font-size: 20px;
  transition: transform 0.2s ease;

  &:focus-within {
    box-shadow: 0px 0px 5px 2px rgb(1, 40, 112);
    transform: translateY(-5px);
  }

  &:active {
    box-shadow: 0px 0px 5px 2px rgb(1, 40, 112);
    transform: translateY(-5px);
  }

  input {
    margin-top: 30px;
    border: none;
    border-bottom: 0.5px solid black;
    padding: 4px;
    font-size: 24px;

    &:focus {
      outline: none;
    }
  }
}

@media (max-width: 1625px) {
  .column-card {
    input {
      margin-top: 15px;
    }
  }
}

@media (max-width: 750px) {
  .column-card {
    display: flex;
    flex-direction: column;
    flex: 1 0 calc(50% - 40px);
    margin: 5px;
    font-size: 18px;

    input {
      margin-top: 20px;
      padding: 0;
      font-size: 20px;
    }
  }
}

@media (max-width: 400px) {
  .column-card {
    display: flex;
    flex-direction: column;
    flex: 1 0 calc(50% - 40px);
    margin: 5px;
    font-size: 15px;

    input {
      padding: 0;
      font-size: 15px;
    }
  }
}

.column-header {
  display: flex;
  justify-content: space-between;
}
</style>
