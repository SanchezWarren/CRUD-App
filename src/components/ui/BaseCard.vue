<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style scoped>
.card {
  background-color: #333333;
  border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    padding: 1rem;
    margin: 2rem auto;
    max-width: 50rem;
    display: flex;
    flex-direction: column;
    border: solid 9px #ff7a00;
    color: white;
}
</style>