<template>
  <div class="container">
    <div class="letters">
      <div class="letter">
        <LetterCard letter="A"></LetterCard>
      </div>
      <div class="timer">
        <p>{{ formattedTime }}</p>
      </div>
    </div>
    <GameTable :columns="columns" @finishGame="finishGame"></GameTable>
  </div>
</template>

<script>
import LetterCard from "~/components/LetterCard.vue";
import GameTable from "~/components/GameTable.vue";
export default {
  components: {
    LetterCard,
    GameTable,
  },
  data() {
    return {
      seconds: 0,
      timer: null,
      columns: [
        {
          id: 123123,
          title: "Animais",
        },
        {
          id: 345,
          title: "Filmes",
        },
        {
          id: 654,
          title: "Carros",
        },
        {
          id: 6456,
          title: "Comida",
        },
        {
          id: 8678,
          title: "Nome",
        },
        {
          id: 978,
          title: "Jogos",
        },
        {
          id: 321,
          title: "Comida",
        },
        {
          id: 4341,
          title: "Nome",
        },
        {
          id: 5235,
          title: "Nome",
        },
      ],
    };
  },
  computed: {
    formattedTime() {
      const minutes = Math.floor((this.seconds % 3600) / 60);
      const seconds = this.seconds % 60;

      return `${this.formatTime(minutes)}:${this.formatTime(seconds)}`;
    },
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.seconds++;
      }, 1000);
    },
    formatTime(value) {
      return value < 10 ? `0${value}` : value;
    },
    finishGame(answers) {
      const body = this.columns.map((column) => {
        return {
          column_id: column.id,
          answer: answers[column.id],
        };
      });

      console.log(body);
    },
  },
  mounted() {
    this.startTimer();
  },
  beforeDestroy() {
    clearInterval(this.timer);
  },
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 40px;
  margin-inline: 20px;
  flex: 1;
  position: relative;
}

.letters {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.timer {
  position: absolute;
  right: 0;
  font-size: 24px;
  padding: 8px;
  margin: 20px;
}

.letter {
  color: var(--primary);
  margin: 10px;
}
</style>
