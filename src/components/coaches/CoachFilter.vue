<template>
  <!-- <base-card> -->
  <nav>
    <h2>Find Your Coach:</h2>
    <span class="filter-option">
      <input type="checkbox" class="btn-check" id="frontend" checked @change="setFilter" />
      <label class="btn btn-outline-secondary" for="frontend">Frontend</label>
    </span>
    <span class="filter-option">
      <input type="checkbox" class="btn-check"  id="backend" checked @change="setFilter" />
      <label class="btn btn-outline-secondary" for="backend">Backend</label>
    </span>
    <span class="filter-option">
      <input type="checkbox" class="btn-check"  id="career" checked @change="setFilter" />
      <label class="btn btn-outline-secondary" for="career">Career</label>
    </span>
  </nav>
 <!--  </base-card> -->
</template>

<script>

export default {
  emits: ['change-filter'],
  data() {
    return {
      filters: {
        frontend: true,
        backend: true,
        career: true
      }
    };
  },
  methods: {
    setFilter(event) {
      const inputId = event.target.id;
      const isActive = event.target.checked;
      const updatedFilters = {
        ...this.filters,
        [inputId]: isActive
      };
      this.filters = updatedFilters;
      this.$emit('change-filter', updatedFilters);
    }
  }
}
</script>

<style scoped>
h2 {
  flex-basis: 25%;
  margin: 1.5rem 0;
  color: grey;
}

.filter-option {
  margin-right: 1rem;
}

.filter-option label,
.filter-option input {
  vertical-align: middle;
}

.filter-option label {
  margin-left: 0.25rem;
}

.filter-option.active label {
  font-weight: bold;
}
nav {
      width: 100%;
    margin: auto 10%;
    display: flex;
    justify-content: left;
    align-items: center;
}

input{
  display: none;
}

.btn{
  padding: 0 2rem;
  cursor: pointer;
}

.btn-outline-secondary:hover {
    color: rgb(0, 0, 0);
    background-color: unset !important;
    border-color: #48b660;
}
.btn-check:checked+.btn-outline-secondary{
  border-color: #48b660;
  border-bottom: #48b660 solid 1px;

}

</style>