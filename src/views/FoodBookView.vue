
<!-- style CSS -->
<!-- Affichage de plusieurs posts sur la page avec menu page1 sur 10-->
<!-- Affichage  des infos du profil sur les likes et commentaires-->



<script setup>
import PostRecette from "../components/PostRecette.vue";
</script>

<script>
export default {
  data() {
    return {
      listPost: [],
      liketest: 2,
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
      console.log("emitréussi");
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
      console.log(this.liketest);
    },

    // Requete pour créer un post
    createPost: async function () {
      //Reccupère le token qui est dans le local storage
      let token = JSON.parse(localStorage.getItem("tokenUserLog"));

      const infoPost = {
        titre: this.infoPost.titre,
        recette: this.infoPost.recette,
      };

      const options = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Authorization: `bearer ${token}`,
        },
        body: JSON.stringify({
          title: infoPost.titre,
          content: infoPost.recette,
        }),
      };
      const response = await fetch(
        "https://social-network-api.osc-fr1.scalingo.io/foodbook/post",
        options
      );
      const data = await response.json();

      if (data.success) {
        await this.getPosts();
      } else {
        alert("Veuillez vous inscrire");
      }

      this.listPost.push(infoPost);
      console.log("increate", this.listPost);

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
          "Authorization": `bearer ${token}`,
        },
        body: JSON.stringify({
          postId: `${reccupid}`,
        }),
      };
      const response = await fetch(
        "https://social-network-api.osc-fr1.scalingo.io/foodbook/post/like",
        options
      );
      const data = await response.json();
      console.log(data);
    },
  },
  addComment: async function () {
    let token = JSON.parse(localStorage.getItem("tokenUserLog"));

    const options = {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        "Authorization": `bearer ${token}`,
      },
      body: JSON.stringify({
        postId: "634f8e99ccaf7f001d9235cb",
        content: "test-commentaire",
      }),
    };
    const response = await fetch(
      "https://social-network-api.osc-fr1.scalingo.io/foodbook/post/comment",
      options
    );
    const data = await response.json();
    console.log(data);
    console.log("reussi");
  },

  computed: {
  //   numberLikeShow: function (arg) {
  //     // this.getPosts()
  //     for (var i = 0; i < this.listPost.length; i++) {
        
  //       if (this.listPost[i]._id == arg) {

  //         console.log("camarche")
  //         return this.listPost[i].likes.length
  //         // dans template :nblike="numberLikeShow"

  //     }
  //   };
  // },
  },
  mounted: function () {
    this.getPosts();
  },
};
</script>

<template>
  <button @click="newPost" type="submit">Créer un post</button>

  <div @submit.prevent="createPost()" v-if="ifcreateposte" class="newpost">
    <form action="">
      <input v-model="this.infoPost.titre" type="text" placeholder="titre" />
      <input
        v-model="this.infoPost.recette"
        type="text"
        placeholder="recette"
      />
      <button type="submit">Envoyer</button>
    </form>
  </div>
  <PostRecette
    @eventCom="addComment()"
    v-for="item in this.listPost"
    :titre="item.title"
    :recette="item.content"
    :nblike="item.likes.length"
    :key="item._id"
  />
  <!-- @some-event="likePosts(item._id)" -->
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


.cardContainer{
  display: flex;
  flex-direction: row;
  margin-top: 30px;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
