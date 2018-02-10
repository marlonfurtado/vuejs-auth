<template>
<div class="section">
  <img src="../assets/logo.png">
  <div class="container login">
    <h3 class="title">Sign In</h3>
    <error-notification v-show="errorCode||errorMessage" :code="errorCode" :message="errorMessage"></error-notification>
    <form name="form" @submit.prevent="validate" novalidate>
      <!-- Email -->
      <div class="field">
        <div class="control has-icons-left has-icons-right">
          <input name="email" type="email" placeholder="Email"
                class="input is-medium"
                :class="{'is-danger':errors.has('email')}"
                v-model="email"
                v-validate="'required|email'">
          <span class="icon is-small is-left">
            <i class="fas fa-envelope"></i>
          </span>
          <!-- Error -->
          <span v-show="errors.has('email')" class="icon is-small is-right">
            <i class="fas fa-exclamation-triangle"></i>
          </span>
          <p v-show="errors.has('email')" class="help is-danger">{{errors.first('email') }}</p>
        </div>
      </div>

      <!-- Password -->
      <div class="field">
        <div class="control has-icons-left has-icons-right">
          <input name="password" type="password" placeholder="Password" 
                class="input is-medium"
                :class="{'is-danger':errors.has('password')}"
                v-model="password" 
                v-validate="'required|min:6'">
          <span class="icon is-small is-left">
            <i class="fas fa-lock"></i>
          </span>
          <!-- Error -->
          <span v-show="errors.has('password')" class="icon is-small is-right">
            <i class="fas fa-exclamation-triangle"></i>
          </span>
          <p v-show="errors.has('password')" class="help is-danger">{{errors.first('password') }}</p>
        </div>
      </div>

      <!-- Login -->
      <div class="field">
        <p class="control">
          <button type="submit" class="button is-medium is-outlined">
            Login
          </button>
        </p>
      </div>
    </form>
    <p class="subtitle is-6 txt-account">You don't have an account? You can <router-link to="/signup">create one!</router-link></p>
  </div>
</div>
</template>

<script>
import firebase from 'firebase'
import ErrorNotification from './ErrorNotification'

export default {
  name: 'login',
  components: {
    ErrorNotification
  },
  data: () => {
    return {
      email: '',
      password: '',
      errorCode: null,
      errorMessage: null
    }
  },
  methods: {
    signIn: function () {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password)
      .then(() => {
        this.$router.replace('home')
      })
      .catch((err) => {
        this.errorCode = err.code
        this.errorMessage = err.message
      })
    },
    validate: function () {
      this.$validator.validateAll()
      .then((result) => {
        if (result) this.signIn()
        return
      })
      .catch((err) => { 
        console.error(err.message)
      })
    }
  },
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
