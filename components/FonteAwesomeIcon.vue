<template>
  <div class="button-icon">
    <div class="icon-circle"></div>
    <font-awesome-icon :icon="['fas', icon]" />
  </div>
</template>

<script>
export default {
  icon: "FonteAwesomeIcon",
  props: {
    icon: {
      default: null,
    },
  },
};
</script>

<style lang="scss" scoped>
.button-icon {
  position: relative;
  margin-left: 20px;
  font-size: 24px;

  .icon-circle {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 32px;
    height: 32px;
    border-radius: 50%;
    transition: background-color 0.3s ease;
    z-index: -1;
  }

  &:hover {
    .icon-circle {
      background-color: rgba(128, 128, 128, 0.123);
      border-radius: 50%;
    }
  }

  &:active {
    .icon-circle {
      background-color: rgb(85, 85, 85);
      border-radius: 50%;
    }
  }
}
</style>
