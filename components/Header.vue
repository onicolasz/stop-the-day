<template>
  <div class="header-container">
    <div class="header-logo">
      <h2>Stop the day</h2>
    </div>
    <div class="header-buttons">
      <FonteAwesomeIcon icon="user"></FonteAwesomeIcon>
      <FonteAwesomeIcon icon="gear"></FonteAwesomeIcon>
    </div>
  </div>
</template>

<script>
import FonteAwesomeIcon from "./FonteAwesomeIcon.vue";
export default {
  name: "Header",
  components: {
    FonteAwesomeIcon,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.header-container {
  color: rgb(1, 40, 112);
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  min-height: 5vh;
  padding: 12px;
  user-select: none;
}

.header-logo {
  text-shadow: 2px 2px 2px #4a99ff;
}

.header-buttons {
  display: flex;
  flex-direction: row;
}
</style>
