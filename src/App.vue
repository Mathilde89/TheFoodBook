<script setup>
import { RouterLink, RouterView } from "vue-router";
import FooterContent from "./components/FooterContent.vue";

import NavBar from "./components/NavBar.vue";

</script>

<template>
  <header>
    <NavBar />
  </header>

  <footer>
    <FooterContent />
  </footer>
</template>

<style lang="scss" scoped>
@font-face {
  font-family: "mardesauve";
  src: url("fonts/marde sauve.otf");
}
@font-face {
  font-family: "OperatorMono";
  src: url(fonts/OperatorMono-BoldItalic.otf);
}
* {
  box-sizing: border-box;
}

#app {
  width: 100vw;
  padding: 0;
  margin: 0;
}
body {
  display: flex;
  margin: 0;
  width: 100vw;
}
.cardContainer {
  display: flex;
  flex-direction: row;
  margin-top: 30px;
  flex-wrap: wrap;
}
</style>
