<template>
  <div id="app">
    <img src="./assets/login.png">
    <router-view @authenticated="setAuthenticated" />
    <router-link v-if="authenticated" to="/HelloWorld"
                 v-on:click.native="logout()" replace>Logout</router-link>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      authenticated: false,
      mockAccount: {
        username: 'admin',
        password: 'admin1',
      },
    };
  },
  mounted() {
    if (!this.authenticated) {
      this.$router.replace({ name: 'HelloWorld' });
    }
  },
  methods: {
    setAuthenticated(status) {
      this.authenticated = status;
    },
    logout() {
      this.authenticated = false;
    },

  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
