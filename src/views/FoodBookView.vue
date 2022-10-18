<script setup>
import PostRecette from "../components/PostRecette.vue";

</script>

<script>

export default {
  data() {
    return {
      listPost:[],
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
      } else this.posteOK= true;


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
    
      // this.infoPost.titre=posts.title
      this.listPost=data.posts
      console.log("listPOst", this.listPost)
    },

    // Requete pour créer un post
    createPost: async function () {
    
      //Reccupère le token qui est dans le local storage
      let token = JSON.parse(localStorage.getItem("tokenUserLog"));
     
      const infoPost= {
        titre: this.infoPost.titre,
        recette: this.infoPost.recette,
      }
      console.log("infopost", infoPost)

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
      console.log("data", data)
      if (data.success) {
          await this.getPosts();
          
        } else {
          alert("Veuillez vous inscrire")
        }

      
      this.listPost.push(infoPost)
      console.log("listPost", this.listPost)

      this.posteOK = true;
      if (this.posteOK == true) {
        this.posteOK = false;
      } else this.posteOK= true;
     
    
    },
    
  },

  // mounted: {
  //   function () { this.getPosts() }


  // }
};
// // //Fait pour pouvoir tester à enlever après le fetch
// const testposterecette1 = {
//   auteur1: "Jane Doe",
//   titre1: "Couscous marocain",
//   recette1:
//     "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
//   date1: "13/10/2022",
//   heure1: "15:40",
//   nblike1: 10,
//   nbcom1: "30",
//   id1: "test1",
//   post1a: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
//   post1b: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
//   post1c: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
// };
// const testposterecette2 = {
//   auteur2: "Titin Milou",
//   titre2: "Pizza",
//   recette2:
//     "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
//   date2: "04/10/2022",
//   heure2: "09:23",
//   nblike2: 1,
//   nbcom2: "1",
//   id2: "test2",
//   post2a: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
//   post2b: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
//   post2c: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
// };
// const testposterecette3 = {
//   auteur3: "Juste Leblanc",
//   titre3: "Quiche",
//   recette3:
//     "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
//   date3: "28/01/2013",
//   heure3: "09:33",
//   nblike3: 42,
//   nbcom3: "20",
//   id3: "test3",
//   post3a: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
//   post3b: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
//   post3c: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
// };

</script>

<template>
  <button @click="newPost" type="submit">Créer un post</button>
  <form @submit.prevent="getPosts()" action="">

    <button  type="submit">Tests</button>
  </form>

  <div @submit.prevent="createPost()" v-if="ifcreateposte" class="newpost">
    <form action="">
      <input v-model="this.infoPost.titre" type="text" placeholder="titre" />
      <input v-model="this.infoPost.recette" type="text" placeholder="recette" />
      <button  type="submit">Envoyer</button>
    </form>
  </div>
  <PostRecette v-for="item in this.listPost" :titre="item.title" :recette="item.content" />

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
  font-size: 0,6em;
}
.nvPost{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>