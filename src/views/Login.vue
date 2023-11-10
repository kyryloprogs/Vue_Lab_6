<template>
    <div>
      <h1>Сторінка "Login"</h1>
      <form @submit="login">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required />
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required />
        <button type="submit">Login</button>
      </form>
    </div>
  </template>
  
  <script>
  import { mapMutations, mapActions, mapState } from 'vuex';
  
  export default {
    data() {
      return {
        email: '',
        password: '',
      };
    },
    computed: {
      ...mapState('auth', ['user', 'isAuthenticated']),
    },
    methods: {
      ...mapMutations('auth', ['setUser', 'setAuthentication']),
      ...mapActions('auth', ['loginUser']),
      async login() {
        try {
          // Використовуйте login в залежності від вашого сервісу автентифікації (Firebase, наприклад)
          const user = { email: this.email, name: 'John Doe' };
          await this.loginUser(user);
          this.$router.push('/todo');
        } catch (error) {
          console.error(error);
        }
      },
    },
  };
  </script>