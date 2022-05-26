<template>
  <div
    :class="
      darkMode === true ? 'container-fluid dark' : 'container-fluid light'
    "
  >
    <DisplayPage />
  </div>
</template>

<script>
// @ is an alias to /src
import DisplayPage from "../components/DisplayPage";
import { mapState } from "vuex";
export default {
  name: "Home",
  components: {
    DisplayPage,
  },
  computed: {
    ...mapState({
      darkMode: (state) => state.booking.darkMode,
    }),
  },
};
</script>
<style scoped>
.dark {
  background-color: white;
  transition: 1s ease-in-out;
}
.light {
  background-color: #3d5f77;
  transition: 1s ease-in-out;
}
</style>
