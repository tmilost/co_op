<script setup>
import coopLogo from "../../public/Co-Operative.png"
import zuhlkeLogo from "../../public/zuhlke_transparent.png"
import giphyCute from "../../public/giphyCute.webp"
import giphy from "../../public/giphy.webp"
import giphyCat from "../../public/giphyCat.webp"

defineProps({
  msg: String,
})

</script>

<template>
  <div class="animation">
    <div class="ghost-animation-one">
      <img class="ghost-cute" :src="giphyCute" alt="giphy">
    </div>
    <div class="ghost-animation-two">
      <img class="ghost" :src="giphy" alt="giphy">
    </div>
    <div class="ghost-animation-three">
      <img class="ghost-cat" :src="giphyCat" alt="giphy">
    </div>
  </div>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="welcome-logo">
      <img class="welcome-logo-coop" :src="coopLogo" alt="coop logo">
      <img class="welcome-logo-zuhlke" :src="zuhlkeLogo" alt="zuhlke logo">
    </div>
  </div>
</template>

<style scoped>
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
    top: 20px;
  }

  100% {
    opacity: 1;
    top: -290px;
  }
}

.ghost-cute {
  width: 100px;
}

.ghost {
  width: 100px;
}

.ghost-cat {
  width: 120px;
}

.hello {
  padding: 25px 35px 55px 35px;
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
}</style>
