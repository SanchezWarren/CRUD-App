<template>
  <footer>
    <nav>
      <img class="figure" alt="profile icon" src="@/assets/header/contact.svg" />
      
    </nav>
  </footer>
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
footer {
  position: relative;
  padding-bottom: 7vh;
  width: 100%;
    background-color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 0.2s linear;
}

footer a {
  text-decoration: none;
  color: #d6f391;
  display: inline-block;
  padding: 0.75rem 1.5rem;
  border: 1px solid transparent;
}

a:active,
a:hover,
a.router-link-active {
  border: 1px solid #d6f391;
}

h3 {
  font-size: 90%;
  color: lightgray;
}
footer nav {
  width: 90%;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

footer ul {
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

.figure{
  width: 90%;
}
</style>