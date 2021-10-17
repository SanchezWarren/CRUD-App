<template>
  <section class="cont">
    <base-card>
      <h2>Page not found</h2>
      <p>
        This page could not be found - maybe check out all our
        <router-link to="/coaches">coaches</router-link>.
      </p>
    </base-card>
  </section>
</template>

<script>
export default{
  mounted () {
    window.scrollTo(0, 0)
  },
}
</script>

<style scoped>
.cont{
  background-color: white;
    padding: 6vh;
  height: 95vh;
  transition: all 0.3s linear;
}

</style>