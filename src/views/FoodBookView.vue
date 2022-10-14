<script setup>
import PostRecette from "../components/PostRecette.vue";
</script>

<script>
//Fait pour pouvoir tester à enlever après le fetch
const testposterecette1 = {
  auteur1: "Jane Doe",
  titre1: "Couscous marocain",
  recette1:
    "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
  date1: "13/10/2022",
  heure1: "15:40",
  nblike1: "10",
  nbcom1: "30",
  id1: "test1",
  post1a:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
  post1b:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
  post1c:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",

};
const testposterecette2 = {
  auteur2: "Titin Milou",
  titre2: "Pizza",
  recette2:
    "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
  date2: "04/10/2022",
  heure2: "09:23",
  nblike2: "1",
  nbcom2: "1",
  id2: "test2",
  post2a:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
  post2b:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
  post2c:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
};
const testposterecette3 = {
  auteur3: "Juste Leblanc",
  titre3: "Quiche",
  recette3:
    "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
  date3: "28/01/2013",
  heure3: "09:33",
  nblike3: "42",
  nbcom3: "20",
  id3: "test3",
  post3a:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
  post3b:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
  post3c:"Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
};

export default {
  data() {
    return {
      testposterecette1,
      testposterecette2,
      testposterecette3,
    };
  },
};
</script>

<template>
  <!-- ["auteur", "titre", "recette", "date", "heure", "nblike", "nbcom", "id", ], -->
  <PostRecette
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
  /> 
</template>
