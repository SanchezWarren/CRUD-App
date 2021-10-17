<template>
  <base-card>
    <img
      class="icon"
      alt="profile icon"
      src="@/assets/profile-solid.svg"
    />
    <h3>{{ fullName }}</h3>
    <h4>${{ rate }}/hour</h4>
    <div class="badge-cont">
      <base-badge
        v-for="area in areas"
        :key="area"
        :type="area"
        :title="area"
      ></base-badge>
    </div>
    <div class="actions">
      <base-button mode="outline" link :to="coachContactLink"
        >Contact</base-button
      >
      <base-button mode="outline" link :to="coachDetailsLink">Details</base-button>
    </div>
  </base-card>
</template>

<script>
import BaseCard from '../ui/BaseCard.vue';
export default {
  components: { BaseCard },
  props: ['id', 'firstName', 'lastName', 'rate', 'areas'],
  computed: {
    fullName() {
      return this.firstName + ' ' + this.lastName;
    },
    coachContactLink() {
      return this.$route.path + '/' + this.id + '/contact'; // /coaches/c1/contact
    },
    coachDetailsLink() {
      return this.$route.path + '/' + this.id; // /coaches/c1
    }
  }
};
</script>

<style scoped>
li {
  margin: 1rem 0;
  border: 1px solid #424242;
  border-radius: 12px;
  padding: 1rem;
}

.icon{
  height: 5rem;
  opacity: 0.2;
}
h3 {
  font-size: 1.5rem;
}

h3,
h4 {
  margin: 0.5rem 0;
  text-align: center;
  color: white;
}
.badge-cont {
  display: flex;
  justify-content: center;
}

div {
  margin: 1.5rem 0;
}

.actions {
  display: flex;
  justify-content: center;
}

@media (max-width: 960px) {
  .actions{
    margin: 0;
  }
}

</style>
