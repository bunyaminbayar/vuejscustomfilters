<template>
  <div>
    <hr />
    <h1>Login</h1>
    <form @submit.prevent="login">
      <label>
        Username:
        <input type="text" v-model="username">
      </label>
      <br>
      <label>
        Password:
        <input type="password" v-model="password">
      </label>
      <br>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    login() {
      if (this.username === 'admin' && this.password === '123') {
        alert('Login successful!')
      } else {
        alert('Invalid username or password')
      }
    }
  }
}
</script>
