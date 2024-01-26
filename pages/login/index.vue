<template>
  <div class="login-container">
    <random-letters color="secondary"></random-letters>
    <div class="login-card">
      <div class="logo">
        <h2>Stop the day</h2>
      </div>
      <div class="input-container">
        <div class="input-field">
          <input v-model="email" type="text" required spellcheck="false" />
          <label>Email</label>
        </div>
        <div class="input-field">
          <input
            v-model="password"
            :type="showPassword"
            required
            spellcheck="false"
          />
          <label>Senha</label>
          <div class="eye-icon" @click="viewPassword">
            <font-awesome-icon
              :icon="['fas', showPassword ? 'eye' : 'eye-slash']"
            />
          </div>
        </div>
      </div>
      <div class="button">
        <button class="btn-finish btn-login" @click="viewPassword">
          Acessar
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import RandomLetters from "~/components/RandomLetters.vue";
export default {
  name: "LoginPage",
  components: { RandomLetters },
  data() {
    return {
      email: null,
      password: null,
      showPassword: false,
    };
  },
  methods: {
    viewPassword() {
      console.log("oi");
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

.input-field {
  position: relative;
  padding-top: 15px;
}

.input-field input {
  width: 350px;
  height: 60px;
  border-radius: 6px;
  font-size: 18px;
  padding: 0 15px;
  border: 2px solid #fff;
  background: transparent;
  color: #fff;
  outline: none;
  margin: 10px 0;
}

.input-field label {
  position: absolute;
  top: 55%;
  left: 15px;
  transform: translateY(-50%);
  color: var(--white);
  font-size: 19px;
  pointer-events: none;
  transition: 0.3s;
}

.input-field .eye-icon {
  position: absolute;
  top: 60%;
  right: 15px;
  transform: translateY(-50%);
  cursor: pointer;
  width: 24px;
  height: 24px;
}

.input-field input:focus ~ label,
.input-field input:valid ~ label {
  top: 12px;
  left: 10px;
  font-size: 16px;
  padding: 0 2px;
}

.input-field input[type="password"] {
  padding-right: 30px;
}

.input-container {
  margin: 60px 0 10px 0;
}
</style>
