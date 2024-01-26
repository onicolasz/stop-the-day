<template>
  <div>
    <random-letters color="secondary"></random-letters>
    <LoginForm></LoginForm>
  </div>
</template>

<script>
import RandomLetters from "~/components/RandomLetters.vue";
import LoginForm from "~/components/Forms/LoginForm.vue";
export default {
  name: "LoginPage",
  components: { RandomLetters, LoginForm },
  data() {
    return {
      email: null,
      password: null,
      showPassword: false,
    };
  },
};
</script>

<style lang="scss" scoped>
div {
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 1;
}
</style>
