<template>
  <img
    class="orange-frame"
    alt="profile icon"
    src="@/assets/header/orange-frame.svg"
  />
  <header>
    <nav>
      <h1>
        <router-link to="/">YourCoach.app</router-link>
      </h1>
      <ul class="options" >

        <li v-if="isLoggedIn">
          <router-link to="/requests">Requests</router-link>
        </li>
        <li v-else>
          <router-link to="/auth">Login</router-link>
        </li>
        <li v-if="isLoggedIn">
          <base-button mode="orange" @click="logout">Logout</base-button>
        </li>
      </ul>
    </nav>
  </header>
  <div class="hero-title">
    <h1>Back to your energie</h1>
    <h6>
      Wanted! Join us, and help us build sugnificant product. We are waiting for
      you.
    </h6>
    <router-link v-if="!isLoggedIn" to="/auth">Register</router-link>
    
    
  </div>
  <img class="figure" alt="profile icon" src="@/assets/header/figure.png" />
  
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
};
</script>

<style scoped>
header {
  position: absolute;
  top: 0px;
  width: 100%;
  height: 7rem;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
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
  margin: auto 8%;
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

.orange-frame {
  padding: 4rem;
    width: 103vh;
    height: 84vh;
    z-index: -1;
}

.hero-title {
  position: absolute;
  top: 13vw;
  left: 8%;
  color: white;
}
.hero-title h1 {
  font-size: 7rem;
}
.hero-title h6 {
  font-size: 1rem;
}

.figure {
  position: absolute;
    right: 2vw;
    width: 70vh;
    z-index: 0;
    transition: all 0.2s linear;
}


@media (max-width: 960px) {

  .orange-frame {
    padding: 1rem;
    height: 120vw;
    width:  auto;
  }
  .figure{
    top: 41vw;
    z-index: 0;
    width: 73vw;
  }
  .hero-title{
    top: 23vw
  }
  .hero-title h1{
    font-size: 13vw;
  }

  .options{
    display: none;
  }
}
</style>
