<template>
<div class="section">
  <img src="../assets/logo.png">
  <div class="container login">
    <h3 class="title">Let's create a new account!</h3>

    <div class="field">
      <p class="control has-icons-left">
        <input class="input is-medium" type="email" placeholder="Email">
        <span class="icon is-small is-left">
          <i class="fas fa-envelope"></i>
        </span>
      </p>
    </div>
    <div class="field">
      <p class="control has-icons-left">
        <input class="input is-medium" type="password" placeholder="Password">
        <span class="icon is-small is-left">
          <i class="fas fa-lock"></i>
        </span>
      </p>
    </div>
    <div class="field">
      <p class="control has-icons-left">
        <input class="input is-medium" type="password" placeholder="Repeat the password">
        <span class="icon is-small is-left">
          <i class="fas fa-lock"></i>
        </span>
      </p>
    </div>
    <div class="field">
      <p class="control">
        <button class="button is-medium is-outlined">
          Sign Up
        </button>
      </p>
    </div>

    <p class="subtitle is-6 txt-account">Go back to <router-link to="/login">login.</router-link></p>
  </div>
</div>
</template>

<script>
export default {
  name: 'signup',
  data: () => {
    return {}
  },
  methods: {}
}
</script>

<style scoped>
@media (min-width: 700px) {
  .login {
    width: 40%;
  }
}
.container {
  margin-top: 30px;
}
.button {
  width: 100%
}
.txt-account {
  margin-top: 40px;
}
</style>
