<script setup>
import { RouterLink, RouterView } from "vue-router";
import FoodBookView from './views/FoodBookView.vue'
</script>

<template>
  <header>
    <div class="navBar">
      <nav class="navCss">
        <RouterLink class="routerLink" to="/">Home</RouterLink>
        <img class="logoNav" src="../src/img/logo.png">
        <RouterLink class="routerLink" to="/inscription">join/log</RouterLink>
      </nav>
    </div>
  </header>

  <div>
    <div class="image-main">
      <img src="../src/img/logo.png">
      <h1>VOTRE RESEAU SOCIAL CULINAIRE PREFERE</h1>
    </div>
  </div>

 <div class="cardContainer">

  <FoodBookView/>

 </div>
  

  
</template>

<style lang="scss" scoped>

*{
  box-sizing: border-box;
  
  font-family: 'Cantata One', serif;
}

#app{
  width: 100vw;
  padding: 0;
  margin: 0;
}
body{
  display: flex;
  margin: 0;
  width: 100vw;
  
}
.navBar{
  @import url('https://fonts.googleapis.com/css2?family=Cantata+One&display=swap');
  font-family: 'Cantata One', serif;
  
  background-color: #D3D3D3;
  color: black;
  font-weight: bold;
  font-size: 1.5em;
  width: 100vw;
  height: 60px;
  border-bottom: 2px solid black;
  text-transform: uppercase;
  
  
 
  .navCss{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    
    
  }

  
  .routerLink{
    display: flex;
    text-decoration: none;
    align-items: center;
    justify-content: space-between;

    &:hover {
      background-color: red;
      color: white;
      border-radius: 5px;
    }
  }
 
  
  .logoNav{
    display: flex;
    width: 55px;
    height: 55px;
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
    width: 100vw;
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
.cardContainer{
  display: flex;
  flex-direction: row;
  margin-top: 30px;
}

</style>





