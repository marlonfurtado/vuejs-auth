<template>
<div class="section">
  <img src="../assets/logo.png">
  <div class="container login">
    <h3 class="title">Sign In</h3>

    <div class="field">
      <p class="control has-icons-left">
        <input class="input is-medium" v-model="email" type="email" placeholder="Email" required>
        <span class="icon is-small is-left">
          <i class="fas fa-envelope"></i>
        </span>
      </p>
    </div>
    <div class="field">
      <p class="control has-icons-left">
        <input class="input is-medium" v-model="password" type="password" placeholder="Password" required>
        <span class="icon is-small is-left">
          <i class="fas fa-lock"></i>
        </span>
      </p>
    </div>
    <div class="field">
      <p class="control">
        <button @click="signIn" class="button is-medium is-outlined">
          Login
        </button>
      </p>
    </div>

    <p class="subtitle is-6 txt-account">You don't have an account? You can <router-link to="/signup">create one!</router-link></p>
  </div>
</div>
</template>

<script>
import firebase from 'firebase'

export default {
  name: 'login',
  data: () => {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    signIn: function () {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password)
      .then(() => {
        this.$router.replace('home')
      })
      .catch((err) => {
        console.log(err)
      })
    }
  }
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
