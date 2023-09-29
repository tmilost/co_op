<script setup>
import coopLogo from "../../public/Co-Operative.png"
import zuhlkeLogo from "../../public/zuhlke_transparent.png"
import giphyCute from "../../public/giphyCute.webp"
import giphy from "../../public/giphy.webp"
import giphyCat from "../../public/giphyCat.webp"
import { computed, ref } from "vue"

defineProps({
  msg: String,
})


let object = {
  sameWeek: {
    document: 30,
    smallParcel: 70,
    largePacel: 90
  },
  twoWeek: {
    document: 10,
    smallParcel: 25,
    largePacel: 30
  }
};
let parcel = ref(0);
let time = ref(0);

const calculatePrice = computed(() => {
  let finalPrice = 0;
  if (parcel.value !== 0 && time.value !== 0) {
    finalPrice = object[parcel.value][time.value];
  }
  return finalPrice;
});

</script>

<template>
  <div class="animation">
    <div class="ghost-animation-one">
      <img class="ghost-cute" :src="giphyCute" alt="giphy" width="100" height="100" rel="preload" fetchpriority="low">
    </div>
    <div class="ghost-animation-two">
      <img class="ghost" :src="giphy" alt="giphy" width="100" height="100" rel="preload" fetchpriority="low">
    </div>
    <div class="ghost-animation-three">
      <img class="ghost-cat" :src="giphyCat" alt="giphy" width="120" height="80" rel="preload" fetchpriority="low">
    </div>
  </div>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <h3>For same week delivery </h3>
    <p> Documents are 40 euros <br> Small parcels are 70 euros <br> Large parcels are 90
      euros</p>
    <h3>For two week deliveries </h3>
    <p> Documents are 10 euros<br> Small parcels are 25 euros <br> Large parcels are 30
      euros</p>
    <select name="parcel" v-model="parcel">
      <option :value="key" v-for="key in Object.keys(object)" :key="key"> {{ key }}</option>
    </select>
    <select name="time" v-model="time" v-if="parcel !== 0">
      <option :value="value" v-for="value in Object.keys(object[parcel])"> {{ value }}</option>
    </select>
    <p>final price = {{ calculatePrice }} euros</p>

    <div class="welcome-logo">
      <img class="welcome-logo-coop" :src="coopLogo" width="100" height="100" alt="coop logo" rel="preload"
        fetchpriority="low">
      <img class="welcome-logo-zuhlke" :src="zuhlkeLogo" width="100" height="100" alt="zuhlke logo" rel="preload"
        fetchpriority="low">
    </div>
  </div>
</template>

<style scoped>
h1 {
  margin-top: 5px;
  margin-bottom: 5px;
}

h3 {
  margin-top: 5px;
  margin-bottom: 5px;

}

.animation {
  display: flex;
}

.ghost-animation-one {
  position: relative;
  animation: floatBubble 5s infinite normal ease-out;
  filter: drop-shadow(0 0 2em rgba(221, 212, 212, 0.39));
}

.ghost-animation-two {
  position: relative;
  animation: floatBubble 4s infinite normal ease-out;
  filter: drop-shadow(0 0 2em rgba(221, 212, 212, 0.39));
}

.ghost-animation-three {
  position: relative;
  animation: floatBubble 6s infinite normal ease-out;
  filter: drop-shadow(0 0 2em rgba(221, 212, 212, 0.39));
}

@keyframes floatBubble {
  0% {
    opacity: 0;
    top: 0px;
  }

  100% {
    opacity: 1;
    top: -290px;
  }
}

.hello {
  padding: 5px 35px 25px 35px;
  background: rgba(255, 255, 255, 0.1);
  box-shadow: 0 26px 42px rgba(221, 212, 212, 0.1);
  border-radius: 25px;
}

.welcome-logo {
  display: flex;
  justify-content: center;
}

.welcome-logo-coop {
  width: 100px;
  will-change: filter;
  transition: filter 300ms;
}

.welcome-logo-coop:hover {
  filter: drop-shadow(0 0 2em #11b2db);
}

.welcome-logo-zuhlke {
  margin-left: 29px;
  width: 100px;
  will-change: filter;
  transition: filter 300ms;
}

.welcome-logo-zuhlke:hover {
  filter: drop-shadow(0 0 2em #995c9d);
}
</style>
