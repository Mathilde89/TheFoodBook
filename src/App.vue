<script setup>
import { RouterLink, RouterView } from "vue-router";
import FoodBookView from './views/FoodBookView.vue'
import FooterContent from './components/FooterContent.vue'
</script>

<script>

export default {
  data() {
    return {
      email: "test@test.com",
      password: "test",
      result: null,
      token: "",
    };
  },
  
  methods:{
    async register(){
      const options = {
        method: "register",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify({
          email: email,
          password: password,
          firstname: firstname,
          lastname: lastname,
          
          
        }),
      };
      const response = await fetch(" https://social-networkapi.osc-fr1.scalingo.io/demo/register ", options);
      const data = await response.json();
    },
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

 <div class="cardContainer" id="cardContainer">

  <FoodBookView/>

 </div>
  
 <footer>
  <FooterContent/>

 </footer>

  
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

  a{
    text-decoration: none;
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
footer{
  width: 100vw;
  background-color: #D3D3D3;
  color: #a52a2a;
  font-weight: bold;
  font-size: 1em;
  width: 100vw;
  height: 60px;
  border-bottom: 2px solid black;
  text-transform: uppercase;
  text-align: center;
  

  
  }

</style>





