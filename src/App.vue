<template>
  <the-header v-if="$route.name!='index'"></the-header>
  <router-view v-slot="slotProps">
    <transition name="route" mode="out-in">
      <component :is="slotProps.Component"></component>
    </transition>
  </router-view>
  <the-footer></the-footer>
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue';
import TheFooter from './components/layout/TheFooter.vue';

export default {
  components: {
    TheHeader,
    TheFooter
  },
  computed: {
    didAutoLogout() {
      return this.$store.getters.didAutoLogout;
    }
  },
  created() {
    this.$store.dispatch('tryLogin');
  },
  watch: {
    didAutoLogout(curValue, oldValue) {
      if (curValue && curValue !== oldValue) {
        this.$router.replace('/coaches');
      }
    }
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html , h3{
  font-family: "Roboto", sans-serif;
  font-weight: 100;

}

body {
  margin: 0;
  height: 100vh;
  background-color: #333333;

  
}

#app{
  max-width: 100%;
  overflow-x: hidden;
}

.route-enter-from {
  opacity: 0;
  transform: translateY(-30px);
}

.route-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.route-enter-active {
  transition: all 0.3s ease-out;
}

.route-leave-active {
  transition: all 0.3s ease-in;
}

.route-enter-to,
.route-leave-from {
  opacity: 1;
  transform: translateY(0);
}

a {
  text-decoration: none;
  color: #333333;
  background-color: white;
  border-radius: 30px;
  display: inline-block;
  padding: 0.45rem 2.5rem;
  border: 1px solid transparent;
  z-index: 10;
}

a:active,
a:hover,
a.router-link-active {
  background-color: transparent;
  border-radius: 30px;
    
  color: #d6f391;
}

</style>