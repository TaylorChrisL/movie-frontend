<script>
export default {
  data: function () {
    return {
      isLoggedIn: false,
    };
  },
  watch: {
    $route: function () {
      this.isLoggedIn = !!localStorage.jwt;
    },
  },
};
</script>
<template>
  <nav>
    <router-link to="/">Home</router-link>
    |
    <router-link to="/movies">All Movies</router-link>
    |
    <router-link to="/movies/new">New Movie</router-link>
    |
    <router-link v-if="!isLoggedIn" to="/signup">Sign Up</router-link>
    |
    <router-link v-if="!isLoggedIn" to="/login">Log In</router-link>
    |
    <router-link v-if="isLoggedIn" to="/logout">Log Out</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
