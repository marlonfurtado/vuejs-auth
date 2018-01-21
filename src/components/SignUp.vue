<template>
<div class="section">
  <img src="../assets/logo.png">
  <div class="container login">
    <h3 class="title">Let's create a new account!</h3>

    <div class="field">
      <p class="control has-icons-left">
        <input class="input is-medium" v-model="email" type="email" placeholder="Email">
        <span class="icon is-small is-left">
          <i class="fas fa-envelope"></i>
        </span>
      </p>
    </div>
    <div class="field">
      <p class="control has-icons-left">
        <input class="input is-medium" v-model="password" type="password" placeholder="Password">
        <span class="icon is-small is-left">
          <i class="fas fa-lock"></i>
        </span>
      </p>
    </div>
    <div class="field is-hidden">
      <p class="control has-icons-left">
        <input class="input is-medium" type="password" placeholder="Repeat the password">
        <span class="icon is-small is-left">
          <i class="fas fa-lock"></i>
        </span>
      </p>
    </div>
    <div class="field">
      <p class="control">
        <button @click="signUp" class="button is-medium is-outlined">
          Sign Up
        </button>
      </p>
    </div>

    <p class="subtitle is-6 txt-account">Go back to <router-link to="/login">login.</router-link></p>
  </div>
</div>
</template>

<script>
import firebase from 'firebase'

export default {
  name: 'signup',
  data: () => {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    signUp: function() {
      console.log('signUp... ')
      const email = this.email
      const password = this.password
      console.log(email)
      console.log(password)
      
      firebase.auth().createUserWithEmailAndPassword(email, password)
      .then((user) => {
        console.log(user)
        alert('Your account has been created!')
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
