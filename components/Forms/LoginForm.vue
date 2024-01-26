<template>
  <div class="login-container">
    <random-letters color="secondary"></random-letters>
    <div class="login-card">
      <div class="logo">
        <h2>Stop the day</h2>
      </div>
      <div class="fields-container">
        <TextInput :value="email" type="email" placeholder="Email"></TextInput>
        <TextInput
          :value="password"
          type="password"
          placeholder="Senha"
        ></TextInput>
      </div>
      <button class="btn-styled" @click="viewPassword">Acessar</button>
    </div>
  </div>
</template>

<script>
import RandomLetters from "~/components/RandomLetters.vue";
import TextInput from "~/components/Forms/TextInput.vue";
export default {
  name: "LoginForm",
  components: { RandomLetters, TextInput },
  data() {
    return {
      email: null,
      password: null,
      showPassword: false,
    };
  },
  methods: {
    viewPassword() {
      this.showPassword = !this.showPassword;
    },
  },
};
</script>

<style lang="scss" scoped>
.logo {
  color: var(--primary);
  font-size: 24px;
  text-shadow: 2px 2px 2px var(--white);
}
.login-container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 1;
}

.login-card {
  padding: 80px 50px;
  background-color: var(--secondary);
  align-items: center;
  justify-content: center;
  display: flex;
  flex-direction: column;
  border-radius: 20px;
  box-shadow: 0 2px 7px var(--black);
  margin: 10px;

  h1 {
    width: 100px;
    height: auto;
  }
}
.fields-container {
  margin: 60px 0 10px 0;
}
</style>
