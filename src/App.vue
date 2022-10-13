<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";

</script>

<template>
  <header>
    <div class="navBar">
      <nav>
        <img src="../src/img/logo.png">
        <RouterLink class="routerLink" to="/">Home</RouterLink>
        <RouterLink class="routerLink" to="/about">About</RouterLink>
        <RouterLink class="routerLink" to="/inscription">Inscription</RouterLink>
        <RouterLink class="routerLink" to="/connexion">Connexion</RouterLink>
      </nav>
    </div>
    
  </header>
  <div>
    <div class="image-main">
      <img src="../src/img/logo.png">
      <h1>VOTRE RESEAU SOCIAL CULINAIRE PREFERE</h1>
    </div>
  </div>

  <RouterView />
  <div class="cardContent">
    
  </div>
</template>

<style lang="scss">

*{
  box-sizing: border-box;
  
  font-family: 'Cantata One', serif;
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
  @import url('https://fonts.googleapis.com/css2?family=Cantata+One&display=swap');
  font-family: 'Cantata One', serif;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  justify-items: center;
  background-color: #D3D3D3;
  color: black;
  font-weight: bold;
  font-size: 1.5em;
  width: 100%;
  height: 60px;
  align-items: center;
  border-bottom: 2px solid black;
  align-content: center;
  text-transform: uppercase;
 
  nav{
    display: flex;
    align-items: center;
    justify-items: center;
    
  }

  
  .routerLink{
    text-decoration: none;
    margin-right: 200px;
    align-items: center;
    &:hover {
      background-color: red;
      color: white;
      border-radius: 5px;
    }
    
    
   
    
  }
  
  img{
    width: 55px;
    height: 55px;
    margin-right: 200px;
    margin-bottom: -3px;
    border-radius: 75px;
    
  }

}

.image-main{
    background-image: url(../src/img/main.jpg);
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
    text-shadow: 0 0 3px white;
  }
  img{
    width: 150px;
    height: 150px;
    border-radius: 75px;
  }  
}

</style>





