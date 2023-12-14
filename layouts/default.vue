<template>
  <div class="app">
    <Header />
    <main>
      <nuxt />
    </main>
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";

export default {
  components: {
    Header,
    Footer,
  },
};
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
  display: flex;
  flex-direction: column;
}
</style>
