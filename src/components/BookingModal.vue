<template>
  <div v-if="city === 'Cape Town'">
    <h1 :class="darkMode === true ? 'sub-heading' : 'sub-heading-darkmode'">
      Availability for
      <span
        :class="darkMode === true ? 'color-word2' : 'color-word2-darkmode'"
        >{{ " " + city }}</span
      >
    </h1>
    <div class="row">
      <div
        class="col-xs-12 col-md-6 col-xl-4"
        v-for="cape in cptAvail"
        :key="cape"
      >
        <img
          class="head-pic mt-3"
          alt="cpt header"
          src="../assets/cpt-light.jpg"
        />
        <span class="dates ms-4 pt-3">{{ cape.date }}</span
        ><br />
        <span
          :class="darkMode === true ? 'status-light' : 'status-dark'"
          v-if="cape.remaining > 0"
          class="status ms-4 pt-3"
          >{{ cape.remaining + " seats left" }}</span
        >
        <span
          :class="darkMode === true ? 'status-light' : 'status-dark'"
          v-else
          class="status ms-4 pt-3"
          >Sold Out</span
        ><br />
        <Button
          @click="toggleDate(cape.date)"
          icon="pi pi-calendar-plus"
          label="Book Now"
          :class="
            darkMode === true
              ? 'p-button-rounded p-button-darkmode ms-4 mt-2'
              : 'p-button-rounded ms-4 mt-2'
          "
          style="width: 12rem"
          :disabled="cape.remaining === 0"
        />
        <br /><br />
      </div>
    </div>
    <Button
      @click="toggleCardsActive"
      label="Go Back"
      :class="
        darkMode === true
          ? 'p-button-rounded p-button-darkmode ms-4 mt-2'
          : 'p-button-rounded ms-4 mt-2'
      "
      style="width: 12rem"
    />
    <br /><br />
  </div>
  <!-- Johannesburg -->

  <div v-if="city === 'Johannesburg'">
    <h1 :class="darkMode === true ? 'sub-heading' : 'sub-heading-darkmode'">
      Availability for
      <span
        :class="darkMode === true ? 'color-word2' : 'color-word2-darkmode'"
        >{{ " " + city }}</span
      >
    </h1>
    <div class="row">
      <div
        class="col-xs-12 col-md-6 col-xl-4"
        v-for="joburg in jhbAvail"
        :key="joburg"
      >
        <img class="head-pic" alt="jhb header" src="../assets/jhb-light.jpg" />
        <span class="dates">{{ joburg.date }}</span
        ><br />
        <span
          :class="darkMode === true ? 'status-light' : 'status-dark'"
          v-if="joburg.remaining > 0"
          class="status ms-4 pt-3"
          >{{ joburg.remaining + " seats left" }}</span
        >
        <span
          :class="darkMode === true ? 'status-light' : 'status-dark'"
          v-else
          class="status ms-4 pt-3"
          >Sold Out</span
        ><br />
        <Button
          @click="toggleDate(joburg.date)"
          icon="pi pi-calendar-plus"
          label="Book Now"
          :class="
            darkMode === true
              ? 'p-button-rounded p-button-darkmode ms-4 mt-2'
              : 'p-button-rounded ms-4 mt-2'
          "
          style="width: 12rem"
          :disabled="joburg.remaining === 0"
        />
        <br /><br />
      </div>
    </div>
    <Button
      @click="toggleCardsActive"
      label="Go Back"
      class="p-button-rounded ms-4 mt-2"
      style="width: 12rem"
    />
  </div>
  <!-- Durban  -->

  <div v-if="city === 'Durban'">
    <h1 :class="darkMode === true ? 'sub-heading' : 'sub-heading-darkmode'">
      Availability for
      <span
        :class="darkMode === true ? 'color-word2' : 'color-word2-darkmode'"
        >{{ " " + city }}</span
      >
    </h1>
    <div class="row">
      <div
        class="col-xs-12 col-md-6 col-xl-4"
        v-for="durbs in dbnAvail"
        :key="durbs"
      >
        <img class="head-pic" alt="dbn header" src="../assets/kzn-light.jpg" />
        <span class="dates">{{ durbs.date }}</span
        ><br />
        <span
          :class="darkMode === true ? 'status-light' : 'status-dark'"
          v-if="durbs.remaining > 0"
          class="status ms-4 pt-3"
          >{{ durbs.remaining + " seats left" }}</span
        >
        <span
          :class="darkMode === true ? 'status-light' : 'status-dark'"
          v-else
          class="status ms-4 pt-3"
          >Sold Out</span
        ><br />
        <Button
          @click="toggleDate(durbs.date)"
          icon="pi pi-calendar-plus"
          label="Book Now"
          :class="
            darkMode === true
              ? 'p-button-rounded p-button-darkmode ms-4 mt-2'
              : 'p-button-rounded ms-4 mt-2'
          "
          style="width: 12rem"
          :disabled="durbs.remaining === 0"
        />
        <br /><br />
      </div>
    </div>
    <br />
    <Button
      @click="toggleCardsActive"
      label="Go Back"
      :class="
        darkMode === true
          ? 'p-button-rounded p-button-darkmode ms-4 mt-2'
          : 'p-button-rounded ms-4 mt-2'
      "
      style="width: 12rem"
    />
  </div>

  <SeatsModal v-if="isModalOpen" />
</template>

<script>
import { mapMutations, mapState } from "vuex";
import Button from "primevue/button";
import SeatsModal from "./SeatsModal.vue";

export default {
  name: "BookingModal",
  data() {
    return {
      remainCPT: [],
      remainJHB: [],
      remainDBN: [],
    };
  },
  components: {
    Button,
    SeatsModal,
  },
  computed: {
    ...mapState({
      dates: (state) => state.booking.dates,
      city: (state) => state.booking.city,
      venue: (state) => state.booking.venue,
      isModalOpen: (state) => state.booking.isModalOpen,
      cptAvail: (state) => state.booking.cptAvail,
      jhbAvail: (state) => state.booking.jhbAvail,
      dbnAvail: (state) => state.booking.dbnAvail,
      darkMode: (state) => state.booking.darkMode,
    }),
  },
  methods: {
    ...mapMutations(["toggleModal", "toggleCardsActive", "toggleDate"]),
  },
  beforeMount() {},
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=PT+Sans:wght@400;700&family=Poppins:wght@100;200;300;400;500;600&display=swap");

/* light mode  */
.p-button {
  margin-left: auto;
  margin-right: auto;
  background-color: #d4af37;
  border-color: #d4af37 !important;
}
.p-button:hover {
  background-color: #3d5f77 !important;
  border-color: #d4af37 !important;
}

.head-pic {
  width: 340px;
  height: 250px;
  border-radius: 20px;
  z-index: -10000;
}
.dates {
  margin-left: auto;
  margin-right: auto;
  position: relative;
  top: -35%;
  transform: translate(-50%, -50%);

  font-family: "Poppins";
  font-style: normal;
  font-weight: 500;
  font-size: 30px;
  text-transform: uppercase;

  color: #ffffff;
}
.sub-heading {
  font-family: "Poppins";
  font-style: normal;
  font-weight: 600;
  /* font-size: 30px;
  text-transform: uppercase; */
  color: #000000;
}
.color-word2 {
  color: #3d5f77;
}
.status-light {
  color: #3d5f77;
}
h1 {
  margin: 30px;
}

@media screen and (max-width: 424px) {
  .sub-heading {
    margin-top: 1rem;
    font-weight: 500;
    font-size: 14px;
    margin-left: auto;
    margin-right: auto;
  }
  .head-pic {
    width: 250px;
    height: 120px;
    margin-left: auto;
    margin-right: auto;
  }
  .dates {
    margin-left: auto;
    margin-right: auto;
    top: -30%;
    transform: translate(-50%, -50%);
    font-size: 20px;
  }
}

/* dark mode  */

.p-button-darkmode {
  margin-left: auto;
  margin-right: auto;
  background-color: #3d5f77;
  border-color: #3d5f77 !important;
}
.p-button-darkmode:hover {
  background-color: #d4af37 !important;
  border-color: #3d5f77 !important;
}
.sub-heading-darkmode {
  font-family: "Poppins";
  font-style: normal;
  font-weight: 600;
  /* font-size: 30px;
  text-transform: uppercase; */
  color: #ffffff;
}
.color-word2-darkmode {
  color: #d4af37;
}

.status-dark {
  color: #d4af37;
}
</style>
