<template>
  <div>
    <form @submit.prevent="register">
      <label for="name">
        Name:
      </label>
      <input v-model="name" type="text" name="name" value>
      <label for="email">
        Email:
      </label>
      <input v-model="email" type="email" name="email" value>

      <label for="password">
        Password:
      </label>
      <input v-model="password" type="password" name value>
      <!-- <p v-if="status === 400">
        Please enter different info.
      </p> -->

      <button type="submit" name="button">
        Register
      </button>

      <p>
        {{ error }}
      </p>

      <div>
        Already have an account? <router-link to="/login">
          Log in
        </router-link>.
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name: '',
      email: '',
      password: '',
      error: null
    }
  },

  methods: {
    register () {
      this.$store.dispatch('register', {
        name: this.name,
        email: this.email,
        password: this.password
      })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
        .catch(err => {
          this.error = err.response.data
        })
    }
  }
}
</script>

<style lang="sass" scoped>
</style>
