<script setup>
import { RouterLink, RouterView } from "vue-router";
import FooterContent from './components/FooterContent.vue'
import FoodBookView from "./views/FoodBookView.vue";
</script>

<script>

export default {
  data() {
    return {
     
    };
  },
  
  
  };
    
</script>

<template>
  <header>
    <div class="navBar">
      <nav class="navCss">
        <img class="logoNav" src="../src/img/logo.png">
        <RouterLink class="routerLink" to="/">Home</RouterLink>
        <a href="#cardContainer">Posts</a>
        <RouterLink  class="routerLink" to="/inscription">join/log</RouterLink> 
        
      </nav>
    </div>
  </header>
  
  <div>
    <div class="image-main">
      <img src="../src/img/logo.png">
      <h1>FOODBOOK</h1>
      <p>votre réseau social culinaire préferé</p> 
    </div>
  </div>
  
  <RouterView />
  <div class="cardContainer" id="cardContainer">
   <FoodBookView/>


   
</div>

 <footer>
  <FooterContent/>

 </footer>

</template>

<style lang="scss" scoped>
@font-face {
      font-family: "mardesauve";
      src: url('fonts/marde sauve.otf');
}
@font-face {
  font-family: "OperatorMono";
  src: url(fonts/OperatorMono-BoldItalic.otf);
}
*{
  box-sizing: border-box;
  
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
  background-color: #D3D3D3;
  color: black;
  font-weight: bold;
  font-size: 1.7em;
  width: 100vw;
  height: 60px;
  border-bottom: 5px solid rgb(7, 69, 2);
  text-transform: uppercase;

  a{
    text-decoration: none;
    color: black;
  }
  
  
 
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
      background-color: rgb(7, 69, 2);
      color: white;
      border-radius: 5px;
    }
   
  }
  a:hover {
    background-color: rgb(7, 69, 2);
    color: white;
    border-radius: 5px;
    }
  
  .logoNav{
    display: flex;
    width: 50px;
    height: 50px;
    border-radius: 75px;
    margin-top: 2px;
  }

}

.image-main{
    background-image: url(../src/img/main.jpg);
    background-position: center;
    background-size: cover;
    text-align: center;
    display: flex;
    flex-direction: column;
    height: 500px;
    border-top: 0;
    width: 100vw;
    align-items: center;
    justify-content: center;
    border-bottom: 5px solid rgb(7, 69, 2);
  h1{
    
    display: flex;
    text-align: center;
    font-size: 3em;
    color: rgb(7, 69, 2);
    margin: 0;
    
    font-family: 'mardesauve', sans-serif;
  }
  p{

    font-size: x-large;
    font-weight: 700;
    font-style: italic;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    text-transform: uppercase;
    text-shadow: -2px 3px 0px white;
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
footer{
  width: 100vw;
  background-color: #D3D3D3;
  color: rgb(7, 69, 2);
  font-weight: bold;
  font-size: 0.8em;
  height: 60px;
  border-bottom: 2px solid black;
  text-transform: uppercase;
  text-align: center;
  border-top: 3.5px solid rgb(7, 69, 2);
  h3{
    margin-top: -2px;
    margin-bottom: 0%;
    border-top: 0px;
    padding: 0%;
  }
  p{
    margin: 0%;
    padding: 0%;
    border: 0px;
  }
  
}

</style>





