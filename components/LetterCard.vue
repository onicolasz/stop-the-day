<template>
  <div class="card">
    <p>{{ subtitle }}</p>
    <h1 class="letter">{{ letter }}</h1>
  </div>
</template>

<script>
export default {
  name: "LetterCard",
  props: {
    subtitle: {
      default: null,
    },
    letter: {
      default: "A",
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  padding: 10px 20px;
  border-radius: 10px;
  background-color: white;
  text-align: center;
  margin: 20px;
  color: rgb(1, 40, 112);
  text-shadow: 2px 2px 2px #4a99ff;
  font-size: 24px;

  p {
    margin-bottom: 20px;
  }
}
</style>
