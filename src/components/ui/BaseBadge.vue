<template>
  <span class="badge" :class="type">
    {{ text }}
  </span>
</template>

<script>
export default {
  props: ['type', 'title'],
  computed: {
    text() {
      return this.title.toUpperCase();
    }
  }
}
</script>

<style scoped>
.badge {
  background-color: #ccc;
  color: #252525;
  font-size: 70%;
  border-radius: 30px;
  padding: 0.2rem 0.6rem;
  display: inline-block;
  width: fit-content;
  margin-right: 0.5rem;
  
}

.aerobic {
  background-color: #ff7a00;
  color: white;
}

.yoga {
  background-color: #ffbc00;
  color: white;
}

.fitness {
  background-color: #989a05;
  color: white;
}
</style>