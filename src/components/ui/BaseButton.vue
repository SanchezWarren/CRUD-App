<template>
  <button v-if="!link" :class="mode">
    <slot></slot>
  </button>
  <router-link v-else :to="to" :class="mode">
    <slot></slot>
  </router-link>
</template>

<script>
export default {
  props: {
    mode: {
      type: String,
      required: false,
      default: null
    },
    link: {
      type: Boolean,
      required: false,
      default: false
    },
    to: {
      type: String,
      required: false,
      default: '/'
    }
  }
}
</script>

<style scoped>
button
{
  text-decoration: none;
  padding: 0.75rem 1.5rem;
  font: inherit;
  background-color: #ff7a00;
  border: 0;
  color: white;
  cursor: pointer;
  border-radius: 30px;
  margin-right: 0.5rem;
  display: inline-block;
}

a:hover,
a:active,
button:hover,
button:active {
  background-color: #bfdd78;
  
} 
 


.flat {
  background-color: white;
  color: #3a0061;
  border: none;
}


.outline {
  background-color: transparent;
  /* border-color: #d6f391;; */
  color: #d6f391;
  margin: 3px;
}
.flat:hover,
.flat:active,
.outline:hover,
.outline:active {
  background-color: white;
  color: #333333;
} 

.orange{
  background-color: #ff7a00;
  color: white;
}


@media (max-width: 960px) {
  button{
    margin-bottom:1vw;
  }

}

</style>