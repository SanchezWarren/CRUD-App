<template>
  <div>
    <base-dialog
      :show="!!error"
      title="An error occurred!"
      @close="handleError"
    >
      <p>{{ error }}</p>
    </base-dialog>
    <section>
      <IndexHeader />
    </section>
    <!-- <section class="flex-list">
      
      <coach-filter @change-filter="setFilters"></coach-filter>
    </section> -->
    <section>
      <h1>Get to know our professional Trainers</h1>
      <img
        class="wave-frame"
        alt="profile icon"
        src="@/assets/header/wave-frame.svg"
      />
      <div class="cont">
        
        <div class="spin-box" v-if="isLoading">
          <base-spinner></base-spinner>
        </div>
        <div class="flex-list" v-else-if="hasCoaches">
          <coach-item
            v-for="coach in filteredCoaches"
            :key="coach.id"
            :id="coach.id"
            :first-name="coach.firstName"
            :last-name="coach.lastName"
            :rate="coach.hourlyRate"
            :areas="coach.areas"
          ></coach-item>
        </div>
        <h3 v-else>No coaches found.</h3>

        <div class="block">
          <h6>
            Become yourself a Trainer in our platform and know how to get more
            from YourCoach.app
          </h6>

          <base-button mode="orange" link to="/register"
            >Register as Coach</base-button
          >
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import CoachItem from '../../components/coaches/CoachItem.vue';
/* import CoachFilter from '../../components/coaches/CoachFilter.vue'; */
/* import IndexHeader from '@/components/layout/IndexHeader.vue'; */
import IndexHeader from '@/components/layout/IndexHeader.vue';

export default {
  components: {
    CoachItem,
    /* CoachFilter, */
    IndexHeader
  },
  data() {
    return {
      isLoading: false,
      error: null,
      activeFilters: {
        frontend: true,
        backend: true,
        career: true
      }
    };
  },
  computed: {
    isLoggedIn() {
      return this.$store.getters.isAuthenticated;
    },
    isCoach() {
      return this.$store.getters['coaches/isCoach'];
    },
    filteredCoaches() {
      const coaches = this.$store.getters['coaches/coaches'];
      return coaches.filter(coach => {
        if (this.activeFilters.frontend && coach.areas.includes('aerobic')) {
          return true;
        }
        if (this.activeFilters.backend && coach.areas.includes('fitness')) {
          return true;
        }
        if (this.activeFilters.career && coach.areas.includes('yoga')) {
          return true;
        }
        return false;
      });
    },
    hasCoaches() {
      return !this.isLoading && this.$store.getters['coaches/hasCoaches'];
    }
  },
  created() {
    this.loadCoaches();
  },
  mounted() {
    window.scrollTo(0, 0);
  },
  methods: {
    setFilters(updatedFilters) {
      this.activeFilters = updatedFilters;
    },
    async loadCoaches(refresh = false) {
      this.isLoading = true;
      try {
        await this.$store.dispatch('coaches/loadCoaches', {
          forceRefresh: refresh
        });
      } catch (error) {
        this.error = error.message || 'Something went wrong!';
      }
      this.isLoading = false;
    },
    handleError() {
      this.error = null;
    }
  }
};
</script>

<style scoped>
.cont {
  background-color: white;
  padding-bottom: 10vh;
  transition: all 0.3s linear;
}

.spin-box{
  height: 44vh;
}
.flex-list {
  margin-top: 32vh;
  position: relative;
  top: -31vh;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  transition: all 0.3s linear;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.controls {
  display: flex;
  justify-content: center;
}

h1 {
  font-size: 3rem;
  color: white;
  margin-top: 0vw;
  margin-bottom: 8vw;
  text-align: center;
}

.wave-frame {
  width: 100%;
  position: absolute;
  z-index: -1;
}

.block h6 {
  font-size: 1rem;
  margin: 2vh;
}

.block {
  position: relative;
  bottom: 20vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  text-align: center;
}

@media (max-width: 960px) {
  h1 {
    margin-top: 16vw;
    font-size: 2rem;
  }

  .flex-list {
    padding: 0 8vw;
  }

  .flex-list .card .actions {
    margin: 0;
  }
}
</style>
