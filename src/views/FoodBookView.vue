<script setup>
import PostRecette from "../components/PostRecette.vue";

</script>

<script>

export default {
  data() {
    return {
      listPost: [],
      liketest:2,
      ifcreateposte: false,
      posteOK: false,
      infoPost: {
        auteur: "",
        titre: "",
        recette: "",
        date: "",
        heure: "",
        nblike: "",
        nbcom: "",
        id: "",
      },
      listCom: [],
    };
  },

  methods: {
    testemit: function () {
      console.log("emitréussi")
    },
    newPost: function () {
      if (this.ifcreateposte == true) {
        this.ifcreateposte = false;
      } else this.ifcreateposte = true;
    },
    postAffiche: function (e) {
      e.preventDefault();
      this.posteOK = true;
      if (this.posteOK == true) {
        this.ifcreateposte = false;
      } else this.posteOK = true;


    },
    // Requete pour lire les posts
    getPosts: async function () {

      const options = {
        method: "GET",
        headers: {
          "Content-Type": "application/json"
        },

      };
      const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/foodbook/posts?page=0&limit=10", options);
      const data = await response.json();


      this.listPost = data.posts
      
      console.log(this.listPost)
      console.log(this.liketest)
      

    },

    // Requete pour créer un post
    createPost: async function () {

      //Reccupère le token qui est dans le local storage
      let token = JSON.parse(localStorage.getItem("tokenUserLog"));

      const infoPost = {
        titre: this.infoPost.titre,
        recette: this.infoPost.recette,
      }


      const options = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "Authorization": `bearer ${token}`
        },
        body: JSON.stringify({
          title: infoPost.titre,
          content: infoPost.recette
        }),



      };
      const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/foodbook/post", options);
      const data = await response.json();

      if (data.success) {
        await this.getPosts();

      } else {
        alert("Veuillez vous inscrire")
      }


      this.listPost.push(infoPost)
      console.log("increate", this.listPost)


      // this.listPost.forEach(element => console.log(element));
      // this.listPost.forEach(element => this.likePosts(element._id));

      this.posteOK = true;
      if (this.posteOK == true) {
        this.posteOK = false;
      } else this.posteOK = true;


    },

    // Requete pour liker les posts
    likePosts: async function (reccupid) {

      //Reccupère le token qui est dans le local storage
      let token = JSON.parse(localStorage.getItem("tokenUserLog"));


      const options = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "Authorization": `bearer ${token}`
        },
        body: JSON.stringify({
          postId: `${reccupid}`,
        }),

      };
      const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/foodbook/post/like", options);
      const data = await response.json();
      console.log(data)
    



    },

  },
  computed: {
    numberLikeShow: async function () {
      // await this.getPosts();
      // return  this.listPost.likes


    },
  },
    mounted:
      function () { this.getPosts() }


};


</script>

<template>
  <button @click="newPost" type="submit">Créer un post</button>
  <form  action="">

    <button   type="submit">Tests</button>
  </form>

  <div @submit.prevent="createPost()" v-if="ifcreateposte" class="newpost">
    <form action="">
      <input v-model="this.infoPost.titre" type="text" placeholder="titre" />
      <input v-model="this.infoPost.recette" type="text" placeholder="recette" />
      <button type="submit">Envoyer</button>
    </form>
  </div>
  <PostRecette @some-event="likePosts(item._id)" v-for="item in this.listPost" :titre="item.title"
    :recette="item.content" :nblike="item.likes.length" :key="item._id" />
    

  <!-- ["auteur", "titre", "recette", "date", "heure", "nblike", "nbcom", "id", ], -->
  <!-- <PostRecette.
    :auteur="testposterecette1.auteur1"
    :titre="testposterecette1.titre1"
    :recette="testposterecette1.recette1"
    :date="testposterecette1.date1"
    :heure="testposterecette1.heure1"
    :nblike="testposterecette1.nblike1"
    :nbcom="testposterecette1.nbcom1"
    :id="testposterecette1.id1"
    :listcompost="testposterecette1.post1a"
  />
  <PostRecette
    :auteur="testposterecette2.auteur2"
    :titre="testposterecette2.titre2"
    :recette="testposterecette2.recette2"
    :date="testposterecette2.date2"
    :heure="testposterecette2.heure2"
    :nblike="testposterecette2.nblike2"
    :nbcom="testposterecette2.nbcom2"
    :id="testposterecette2.id2"
    :listcompost="testposterecette2.post2a"
  />
  <PostRecette
    :auteur="testposterecette3.auteur3"
    :titre="testposterecette3.titre3"
    :recette="testposterecette3.recette3"
    :date="testposterecette3.date3"
    :heure="testposterecette3.heure3"
    :nblike="testposterecette3.nblike3"
    :nbcom="testposterecette3.nbcom3"
    :id="testposterecette3.id3"
    :listcompost="testposterecette3.post3a"

  ["auteur", "titre", "recette", "date", "heure", "nblike", "nbcom", "id", ],
  <PostRecette :auteur="testposterecette1.auteur1" :titre="testposterecette1.titre1"
    :recette="testposterecette1.recette1" :date="testposterecette1.date1" :heure="testposterecette1.heure1"
    :nblike="testposterecette1.nblike1" :nbcom="testposterecette1.nbcom1" :id="testposterecette1.id1"
    :listcompost="testposterecette1.post1a" />
  <PostRecette :auteur="testposterecette2.auteur2" :titre="testposterecette2.titre2"
    :recette="testposterecette2.recette2" :date="testposterecette2.date2" :heure="testposterecette2.heure2"
    :nblike="testposterecette2.nblike2" :nbcom="testposterecette2.nbcom2" :id="testposterecette2.id2"
    :listcompost="testposterecette2.post2a" />
  <PostRecette :auteur="testposterecette3.auteur3" :titre="testposterecette3.titre3"
    :recette="testposterecette3.recette3" :date="testposterecette3.date3" :heure="testposterecette3.heure3"
    :nblike="testposterecette3.nblike3" :nbcom="testposterecette3.nbcom3" :id="testposterecette3.id3"
    :listcompost="testposterecette3.post3a" /> -->
</template>

<style scoped>
button {
  width: 100px;
  height: 50px;
  border-radius: 10px;
  background-color: rgb(7, 69, 2);
  color: white;
  font-size: 0, 6em;
}

.nvPost {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>