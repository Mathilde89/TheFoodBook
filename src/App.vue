<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";

</script>

<template>
  <header>
    <div class="navBar">
      <nav>
        <img src="../src/components/img/main.png">
        <RouterLink class="routerLink" to="/">Home</RouterLink>
        <RouterLink class="routerLink" to="/about">About</RouterLink>
        <RouterLink class="routerLink" to="/inscription">Inscription</RouterLink>
        <RouterLink class="routerLink" to="/connexion">Connexion</RouterLink>
      </nav>
    </div>
    
  </header>
  <div>
    <div class="image-main">
      <img src="../src/components/img/logo.png">
      <h1>VOTRE RESEAU SOCIAL CULINAIRE PREFERE</h1>
    </div>
  </div>

  <RouterView />
</template>

<style lang="scss">

*{
  box-sizing: border-box;
}
#app{
  width: 100%;
}
body{
  display: flex;
  margin: 0;
  width: 100%;
  
}
.navBar{
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
  margin-right: 20px;
  align-items: center;
  border-bottom: 2px solid black;
  align-content: center;
  nav{
    align-items: center;
    justify-items: center;
  }

  
  .routerLink{
    text-decoration: none;
    margin-right: 100px;
    align-items: center;
    
   
    
  }
  
  img{
    width: 60px;
    height: 60px;
  }

}

.image-main{
    background-image: url(../src/components/img/main.jpg);
    text-align: center;
    display: flex;
    flex-direction: column;
    height: 600px;
    border-top: 0;
    align-items: center;
    justify-content: center;
  h1{
    display: flex;
    text-align: center;
    font-size: 3em;
    color: black;
    margin: 0;
    font-family: 'Cantata One', serif;
  }
  img{
    width: 150px;
    height: 150px;
  }  
}

</style>





