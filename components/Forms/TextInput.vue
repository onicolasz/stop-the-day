<template>
  <div class="text-input">
    <input :type="type" :value="value" @input="onInput" />
    <label>{{ placeholder }}</label>
  </div>
</template>

<script>
export default {
  name: "TextInput",
  props: {
    type: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
  },
  date() {
    return {
      showPassword: false,
    };
  },
  methods: {
    onInput(event) {
      this.$emit("input", event.target.value);
    },
    viewPassword() {
      this.showPassword = !this.showPassword;
    },
  },
};
</script>

<style>
.text-input {
  position: relative;
  padding-top: 15px;
}

input {
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

input:focus ~ label,
input:valid ~ label {
  top: 12px;
  left: 10px;
  font-size: 16px;
  padding: 0 2px;
}

input[type="password"] {
  padding-right: 30px;
}

label {
  position: absolute;
  top: 55%;
  left: 15px;
  transform: translateY(-50%);
  color: var(--white);
  font-size: 19px;
  pointer-events: none;
  transition: 0.3s;
}

/*
.password-icon {
  position: absolute;
  top: 60%;
  right: 15px;
  transform: translateY(-50%);
  cursor: pointer;
  width: 24px;
  height: 24px;
}
*/
</style>
