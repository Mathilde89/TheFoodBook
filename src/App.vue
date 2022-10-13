<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <header>
    

    <div class="NavBar">
      <nav>
        <RouterLink class="routerLink" to="/">Home</RouterLink>
        <RouterLink class="routerLink" to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style lang="scss">
#app{
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  justify-items: center;
  background-color: lightgray;
  color: black;
  font-weight: bold;
  font-size: 1.3em;
  width: 100%;
  height: 60px;
  margin-right: 10px;
  align-items: center;

  .routerLink{
    text-decoration: none;

  }
}
</style>





