<template>
  <header>
    <nav>
      <h1>
        <router-link to="/">YourCoach.app</router-link>
      </h1>
      <ul>
        
        <li v-if="isLoggedIn">
          <router-link to="/requests">Requests</router-link>
        </li>
        <li v-else>
          <router-link to="/auth">Login</router-link>
        </li>
        <li v-if="isLoggedIn">
          <base-button @click="logout">Logout</base-button>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  computed: {
    isLoggedIn() {
      return this.$store.getters.isAuthenticated;
    }
  },
  methods: {
    logout() {
      this.$store.dispatch('logout');
      this.$router.replace('/coaches');
    }
  }
}
</script>

<style scoped>
header {
  width: 100%;
  height: 5vh;
  background-color: #ff7a00;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: all 1.3 linear;
}


h1 {
  margin: 0;
}

h1 a {
  background-color: transparent;
  color: white;
  margin: 0;
  padding: 0;
}

h1 a:hover,
h1 a:active,
h1 a.router-link-active {
  border-color: transparent;
}


header nav {
  width: 100%;
    margin: auto 10%;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

header ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

li {
  margin: 0 0.5rem;
}


@media (max-width: 960px) {
  header{
    height:12vh;
  }

  header nav{
    flex-direction: column;
    align-items: start;

  }
}
</style>