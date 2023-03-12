<script>
export default {
  data() {
    return {
      // bool est utilisé pour afficher la liste des posts quand clique sur le bouton
      bool: false,
      addlike: 0,
      listPost: [],
      com: "",
    };
  },
  emits: ["eventCom", "someEvent", "sendComment"],

  //Ici ce sont les données liés à un post
  props: [
    "auteur",
    "titre",
    "recette",
    "date",
    "heure",
    "nblike",
    "nbcom",
    "click",
    "msgBody",
    "key",
    "listcom",
  ],

  methods: {
    getPosts: async function () {
      const options = {
        method: "GET",
        headers: {
          "Content-Type": "application/json",
        },
      };
      const response = await fetch(
        "https://social-network-api.osc-fr1.scalingo.io/foodbook/posts?page=0&limit=10",
        options
      );
      const data = await response.json();

      this.listPost = data.posts;

      console.log(this.listPost);
    },

    //Fonction pour afficher ou non la div contenant la liste des posts
    clickCom: function () {
      let token = JSON.parse(localStorage.getItem("tokenUserLog"));
      if (token == null) {
        alert("Vous devez vous connectez pour pouvoir commenter");
      } else {
        if (this.bool == true) {
          this.bool = false;
        } else this.bool = true;
      }
    },
  },
};
</script>

<template>
    
    
  <div class="main">
    <ul class="cards">
      <li class="cards_item">
        <div class="card">
          <div class="card_image">
            <img
              src="https://assets.codepen.io/652/photo-1468777675496-5782faaea55b.jpeg"
              alt="mixed vegetable salad in a mason jar."
            />
          </div>
          <div class="card_content">
            <h2 class="card_title"> {{ titre }}</h2>
            <div class="card_text">
              <p>
                {{ recette }}
              </p>
            </div>
            <div class="footerpost">
        <div class="like">
          <form action="">
            <button @click.prevent="$emit('someEvent')">
              <i class="fa-solid fa-heart"></i>
            </button>
          </form>
          <div class="nblike">
            {{ nblike }} <i class="fa-solid fa-heart"></i>
          </div>
        </div>
        <div class="com">
          <button @click="clickCom" class="buttoncom">
            <i class="fa-solid fa-comments"></i>
          </button>
          <div class="nbcom">{{ nbcom }} commentaires</div>
        </div>
      </div>
      <div v-if="bool" class="listcomcontainer">
      <form action="">
        <input
          v-model="this.com"
          type="text"
          placeholder="A vos commentaires!"
        />
        <button
          @click.prevent="$emit('sendComment', this.com)"
          class="buttoncomvalid"
        >
          <i class="fa-solid fa-share"></i>
        </button>
      </form>
      <div v-for="item in listcom" class="listcom">
        <div class="auteurdate">
          <h2>{{ item.firstname }}</h2>
          a écrit :
        </div>
        <p>
          {{ item.content }}
        </p>
      </div>
    </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
body {
  font-family: "Oxygen", sans-serif;
  color: #050505;
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

.main {
  max-width: 1200px;
  margin: 0 auto;
}

.cards {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
  margin: 0;
  padding: 0;
}

.cards_item {
  display: flex;
  padding: 1rem;
}

.card_image {
  position: relative;
  max-height: 250px;
}

.card_image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}



@media (min-width: 40rem) {
  .cards_item {
    width: 50%;
  }
}

@media (min-width: 56rem) {
  .cards_item {
    width:70%;
  }
}

.card {
  background-color: white;
  border-radius: 0.25rem;
  box-shadow: 0 20px 40px -14px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.card_content {
  position: relative;
  padding: 16px 12px 32px 24px;
  margin: 16px 8px 8px 0;
  max-height: 290px;
  overflow-y: scroll;
}

.card_content::-webkit-scrollbar {
  width: 8px;
}

.card_content::-webkit-scrollbar-track {
  box-shadow: 0;
  border-radius: 0;
}

.card_content::-webkit-scrollbar-thumb {
  background: #c89b3f;
  border-radius: 15px;
}

.card_title {
  position: relative;
  margin: 0 0 24px;
  padding-bottom: 10px;
  text-align: center;
  font-size: 20px;
  font-weight: 700;
}

.card_title::after {
  position: absolute;
  display: block;
  width: 50px;
  height: 2px;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  background-color: #c89b3f;
  content: "";
}

hr {
  margin: 24px auto;
  width: 50px;
  border-top: 2px solid #c89b3f;
}

.card_text p {
  margin: 0 0 24px;
  font-size: 14px;
  line-height: 1.5;
}

.card_text p:last-child {
  margin: 0;
}
button{margin-top: 10px;}

i{margin-top: 10px;}

.nbcom{margin-top: 10px;}
</style>
