<template>
  <nav
    class="navbar bg-light sticky-top"
    :class="
      darkMode === true
        ? 'navbar bg-light sticky-top navbar-darkmode'
        : 'navbar bg-light sticky-top'
    "
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="/">
        <img
          src="../assets/Sharenet_Logo-removebg-preview.png"
          alt=""
          class="d-inline-block align-text-top logo"
        />
      </a>
      <!-- <button @click="toggleMode" :class="darkMode === true ? 'sun' : 'moon'"> -->
      <i v-if="!darkMode" class="pi pi-sun" @click="toggleMode"></i>
      <i v-if="darkMode" class="pi pi-moon" @click="toggleMode"></i>
      <!-- </button> -->
    </div>
  </nav>
</template>

<script>
import { mapMutations, mapState } from "vuex";
export default {
  computed: {
    ...mapState({
      darkMode: (state) => state.booking.darkMode,
    }),
  },
  methods: {
    ...mapMutations(["toggleMode"]),
  },
};
</script>

<style scoped>
.navbar {
  background-color: #6da0aa !important;
  transition: 1s ease-in-out;
}
.pi-sun {
  cursor: pointer;
  font-size: 40px;
  color: white;
}
.pi-moon {
  cursor: pointer;
  font-size: 40px;
  color: black;
}
@media screen and (max-width: 430px) {
  .logo {
    width: 150px;
    height: 30px;
  }
}

/* dark mode  */
.navbar-darkmode {
  background-color: #3d5f77 !important;
  transition: 1s ease-in-out;
}
</style>
