<template>
  <div class="random-letters-container">
    <div
      v-for="letter in randomLetters"
      :key="letter.id"
      class="random-letter"
      :style="{
        top: letter.top,
        left: letter.left,
        '--delay': letter.animationDelay + 's',
        '--translateX': letter.translateX,
        '--translateY': letter.translateY,
        color: `var(--${color})`,
      }"
    >
      {{ letter.value }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    color: {
      default: "--black",
    },
  },
  data() {
    return {
      randomLetters: [],
    };
  },
  methods: {
    createRandomLetters() {
      const numLetters = 50;

      for (let i = 0; i < numLetters; i++) {
        this.randomLetters.push({
          id: i,
          value: this.getRandomLetter(),
          top: `${Math.random() * 100}vh`,
          left: `${Math.random() * 100}vw`,
          translateX: Math.random() * 20 - 10,
          translateY: Math.random() * 20 - 10,
          animationDelay: Math.random() * 5,
        });
      }
    },
    getRandomLetter() {
      const alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      return alphabet[Math.floor(Math.random() * alphabet.length)];
    },
  },
  mounted() {
    this.createRandomLetters();
  },
};
</script>

<style lang="scss" scoped>
.random-letters-container {
  z-index: -1;
  position: absolute;
  height: 100vh;
  width: 100vw;
}

.random-letter {
  position: absolute;
  margin: 10px;
  font-size: 24px;
  animation: moveAndChange 4s infinite alternate ease-in-out;
  animation-delay: calc(var(--delay) * 1s);
}

@keyframes moveAndChange {
  0%,
  100% {
    opacity: 1;
    transform: translate(0, 0);
  }
  50% {
    opacity: 0;
    transform: translate(
      calc(var(--translateX) * 1px),
      calc(var(--translateY) * 1px)
    );
  }
}
</style>
