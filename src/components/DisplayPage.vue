<template>
<br><br>
  <section :class="darkMode === true ? 'section1' : 'section1-darkmode'">
    <p class="main-heading">
      WELCOME TO<br />SHARENET'S <span :class="darkMode === true ? 'color-word' : 'color-word-darkmode'">CRYPTO</span> WORKSHOP
    </p>
    <p :class="darkMode === true ? 'text-darkmode' : 'text'">
      At the end of this workshop you’ll know the rules of thumb to follow
      across all of the fundamental of Crypto and the tech behind it all. You’ll
      be less likely to be fooled because you understand the history, the theory
      and the best practices to apply and trade safely.
    </p>
  </section>
  <section class="section2">
        <BookingModal v-if="!cardsActive" />
    <div class="row">
      <h2 :class="darkMode === true ?'sub-heading-darkmode mt-3' : 'sub-heading mt-3'" v-if="cardsActive">
        Select A <span :class="darkMode === true? 'color-word2' : ' color-word2-darkmode'">City</span>
      </h2>
      <div class="col-xs-12 col-md-6 col-xl-4 mt-4">
        <div v-if="cardsActive" class="cards">
          <img class="head-pic" alt="cpt header" src="../assets/cpt.jpg" />
          <h3 class="city mt-2">Cape Town</h3>
          <Button
            @click="toggleCityCPT"
            class="p-button-rounded mb-4 p-2"
            icon="pi pi-eye"
            label="View More"
          />
        </div>
      </div>
      <div class="col-xs-12 col-md-6 col-xl-4 mt-4">
        <div v-if="cardsActive" class="cards">
          <img class="head-pic" alt="jhb header" src="../assets/jhb.jpg" />
          <h3 class="city mt-2">Johannesburg</h3>
          <Button
            @click="toggleCityJHB"
            class="p-button-rounded mb-4 p-2"
            icon="pi pi-eye"
            label="View More"
          />
        </div>
      </div>
      <div class="col-xs-12 col-md-6 col-xl-4 mt-4">
        <div v-if="cardsActive" class="cards">
          <img class="head-pic" alt="dbn header" src="../assets/kzn.jpg" />
          <h3 class="city mt-2">Durban</h3>
          <Button
            @click="toggleCityKZN"
            class="p-button-rounded mb-4 p-2"
            icon="pi pi-eye"
            label="View More"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { mapState, mapMutations } from "vuex";
import Button from "primevue/button";
import BookingModal from "./BookingModal.vue";
export default {
  name: "DisplayPage",
  components: {
    BookingModal,
    Button,
  },
  computed: {
    ...mapState({
      cardsActive: (state) => state.booking.cardsActive,
      darkMode: (state) => state.booking.darkMode
    }),
  },
  methods: {
    ...mapMutations(["toggleCityCPT", "toggleCityKZN", "toggleCityJHB"]),
  },
};
</script>

<style scoped>
/* light mode  */
.section1 {
  width: 100%;
  height: 400px;
  padding-top: 2rem;
  object-fit: cover;
  background-image: linear-gradient(
      90deg,
      #3d5f77 0%,
      rgba(61, 95, 119, 0.75) 74.71%,
      rgba(61, 95, 119, 0) 159.37%
    ),
    url("../assets/home-bg.jpg");
  background-size: cover;
  border-radius: 20px;
  z-index: -100000;
  margin-left: auto;
  margin-right: auto;
}
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
  width: 359.29px;
  height: 250px;
  border-radius: 20px;
}
.main-heading {
padding-top: 5rem;
  margin-left: 3rem;
  font-family: "Poppins";
  font-style: normal;
  font-weight: 600;
  font-size: 32px;
  text-align: left;
  text-transform: uppercase;
  color: #ffffff;
}
.city {
  margin-left: auto;
  margin-right: auto;
}
.sub-heading {
  font-family: "Poppins";
  font-style: normal;
  font-weight: 600;
  font-size: 30px;
  text-transform: uppercase;
  color: white;
}
.color-word2 {
  color: #3d5f77;
}
.text {
  font-family: "Poppins";
  font-style: normal;
  font-weight: 400;
  width: 75%;
  font-size: 16px;
  color: #ffffff;
  margin-left: 3rem;
}
.color-word {
  color: #d4af37;
}
.cards {
  border-radius: 20px;
}

@media screen and (max-width: 768px) {
.section1 {
    width: 100%;
    height: 300px;
    top: 70px;
  }
    .main-heading {
    font-size: 28px;
    text-align: left;
    margin-left: 0.7rem;
    padding-top: 30px;
  }
  .text {
    font-family: "Poppins";
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    width: 65%;
    margin-left: 1rem;
  }

}

@media screen and (max-width: 430px) {
  .section1 {
    width: 300px;
    height: 150px;
    top: 70px;
  }
  .card {
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 150px;
  }
  .main-heading {
    font-size: 14px;
    top: 350px !important;
  }
  .text {
    font-family: "Poppins";
    font-style: normal;
    font-weight: 400;
    font-size: 8px;
    width: 280px;
    margin-left: 0.7rem;
  }
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
  .city {
    margin-left: auto;
    margin-right: auto;
  }
}

/* dark mode  */
.section1-darkmode {
  width: 100%;
  height: 400px;
  padding-top: 2rem;
  object-fit: cover;
  background-image: linear-gradient(90deg, #D4AF37 0%, rgba(212, 175, 55, 0) 159.37%),
    url("../assets/home-bg.jpg");
  background-size: cover;
  border-radius: 20px;
  z-index: -100000;
  margin-left: auto;
  margin-right: auto;
}
.p-button-darkmode {
  margin-left: auto;
  margin-right: auto;
 background-color: #3d5f77;
  border-color: #3d5f77 !important;
}
.p-button-darkmode:hover {
  background-color:#d4af37 !important;
  border-color:  #3d5f77 !important;
}

.sub-heading-darkmode {
  font-family: "Poppins";
  font-style: normal;
  font-weight: 600;
  font-size: 30px;
  text-transform: uppercase;
  color: black;
}
.color-word2-darkmode {
  color: #d4af37;
}
.text-darkmode {
  font-family: "Poppins";
  font-style: normal;
  font-weight: 400;
  width: 75%;
  font-size: 16px;
  color: #ffffff;
  margin-left: 3rem;
}
.color-word-darkmode {
  color: #3d5f77;
}
</style>
