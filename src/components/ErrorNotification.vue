<template>
  <div id="notification" class="notification is-danger">
    <button @click="close" class="delete"></button>
    <p>Code: {{code || '0'}}</p>
    <p>{{message || 'Sorry, an error occurred.'}}</p>
    <p>Try again, or <router-link to="/signup">create account.</router-link></p>
  </div>
</template>

<script>
export default {
  name: 'error-notification',
  props: ['code', 'message'],
  data: () => {
    return {}
  },
  methods: {
    close: function() {
      document.querySelector('#notification').classList.add('is-hidden')
    }
  }
}
</script>

<style>

</style>
