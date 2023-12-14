<template>
  <div class="gamemode-container">
    <random-letters></random-letters>
    <div class="mode-title">
      <h1>Escolha o modo de jogo</h1>
    </div>
    <div class="gamemode-buttons">
      <div class="gamemode">
        <button @click="setGameMode('normal')" :disabled="hasPlayed.normal">
          <h1>Normal</h1>
        </button>
        <p v-if="hasPlayed.normal">
          Você já jogou hoje <br /><br />
          Espere {{ timeUntilNextDay }}
        </p>
      </div>
      <div class="gamemode">
        <button @click="setGameMode('double')" :disabled="hasPlayed.double">
          <h1>Duplo</h1>
        </button>
        <p v-if="hasPlayed.double">
          Você já jogou hoje <br /><br />
          Espere {{ timeUntilNextDay }}
        </p>
      </div>
    </div>
    <Ranking :ranking="ranking"></Ranking>
  </div>
</template>

<script>
import RandomLetters from "~/components/RandomLetters.vue";
export default {
  components: { RandomLetters },
  data() {
    return {
      randomLetters: [],
      startTime: null,
      timeUntilNextDay: "00:00:00",
      hasPlayed: {
        normal: false,
        double: false,
      },
      ranking: [
        {
          name: "Nicolas",
          position: 1,
          time: "01:59.000",
        },
        {
          name: "Gustavo",
          position: 2,
          time: "01:59.000",
        },
        {
          name: "Paulo",
          position: 3,
          time: "01:59.000",
        },
        {
          name: "Natalia",
          position: 4,
          time: "01:59.000",
        },
        {
          name: "Dessa",
          position: 5,
          time: "01:59.000",
        },
        {
          name: "Paulo",
          position: 6,
          time: "01:59.000",
        },
        {
          name: "Natalia",
          position: 7,
          time: "01:59.000",
        },
        {
          name: "Dessa",
          position: 8,
          time: "01:59.000",
        },
      ],
    };
  },
  methods: {
    setGameMode(mode) {
      this.$router.push({ path: `/game/${mode}/1` });
    },
    setStartTimeForNextDay() {
      const now = new Date();

      const nextDay = new Date(now);
      nextDay.setDate(now.getDate() + 1);
      nextDay.setHours(0, 0, 0, 0);

      this.startTime = nextDay;
    },
    updateTimeUntilNextDay() {
      const now = new Date();
      const targetTime = new Date(this.startTime);

      if (now > targetTime) {
        targetTime.setDate(targetTime.getDate() + 1);
      }

      const timeDifference = targetTime - now;

      const hours = Math.floor(timeDifference / (1000 * 60 * 60));
      const minutes = Math.floor(
        (timeDifference % (1000 * 60 * 60)) / (1000 * 60)
      );
      const seconds = Math.floor((timeDifference % (1000 * 60)) / 1000);

      this.timeUntilNextDay = `${this.pad(hours)}:${this.pad(
        minutes
      )}:${this.pad(seconds)}`;
    },
    pad(value) {
      return value < 10 ? `0${value}` : value;
    },
  },
  mounted() {
    this.setStartTimeForNextDay();
    this.updateTimeUntilNextDay();

    setInterval(() => {
      this.updateTimeUntilNextDay();
    }, 1000);
  },
};
</script>

<style lang="scss" scoped>
.gamemode-container {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: var(--primary);
  height: 100%;
  user-select: none;
  position: relative;
}

.gamemode-buttons {
  display: flex;
  flex-direction: row;
  margin-bottom: 5%;
}

.mode-title {
  margin: 40px;
  text-shadow: 2px 2px 2px var(--secondary);
  animation: float 3s ease-in-out infinite;

  h1 {
    padding: 10px;
  }
}

@keyframes float {
  0%,
  100% {
    transform: translatey(0);
  }
  50% {
    transform: translatey(-20px);
  }
}

.gamemode {
  p {
    text-align: center;
    color: grey;
  }

  button {
    color: var(--primary);
    padding: 12px 20px;
    border: 2px solid var(--primary);
    border-radius: 10px;
    margin: 25px;
    font-size: 14px;
    box-shadow: 2px 2px 8px var(--black);
    background-color: var(--white);
    text-shadow: 2px 2px 2px var(--secondary);
    transition: all 0.2s ease;
    cursor: pointer;

    &:not(:disabled) {
      &:hover {
        transform: translateY(-5px);
        background-color: var(--primary);
        color: var(--white);
        text-shadow: 2px 3px 2px var(--secondary);
      }

      &:active {
        transform: translateY(0px);
        text-shadow: 2px 2px 2px var(--secondary);
        box-shadow: 0 2px 7px var(--black);
      }
    }

    &:disabled {
      box-shadow: 0 0 0;
      border: 2px solid grey;
      text-shadow: 0 0 0;
      color: grey;
    }
  }
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
    align-items: center;
  }

  .gamemode {
    button {
      font-size: 10px;
    }
  }
}
</style>
