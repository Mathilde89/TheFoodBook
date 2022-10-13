<script setup>

import PostRecette from "../components/PostRecette.vue";

</script>

<script>
 
 //Fait pour pouvoir tester à enlever après le fetch
 const testposterecette1={
    auteur1:"Jane Doe",
    titre1:"Couscous marocain",
    recette1:"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
    date1:"13/10/2022",
    heure1:"15:40",
    nblike1:"10",
    nbcom1:"30",
    id1:"test1",
 };
 const testposterecette2={
    auteur2:"Titin Milou",
    titre2:"Pizza",
    recette2:"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
    date2:"04/10/2022",
    heure2:"09:23",
    nblike2:"1",
    nbcom2:"1",
    id2:"test2",
 };
 const testposterecette3={
    auteur3:"Juste Leblanc",
    titre3:"Quiche",
    recette3:"Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore cumque quaerat ea laborum quod minima. Quisquam dolores sapiente, facilis deserunt minima sed recusandae itaque ducimus alias quos odit culpa debitis.",
    date3:"28/01/2013",
    heure3:"09:33",
    nblike3:"42",
    nbcom3:"20",
    id3:"test3",
 };

</script>

<template>
<!-- ["auteur", "titre", "recette", "date", "heure", "nblike", "nbcom", "id", ], -->
    <PostRecette 
    :auteur="this.auteur1" 
    :titre="this.testposterecette1.titre1"
    :recette="this.testposterecette1.recette1"
    :date="this.testposterecette1.date1"
    :heure="this.testposterecette1.heure1"
    :nblike="this.testposterecette1.nblike1"
    :nbcom="this.testposterecette1.nbcom1"
    :id="this.testposterecette1.id1"
    />
    <PostRecette 
    :auteur="this.auteur2" 
    :titre="this.testposterecette2.titre2"
    :recette="this.testposterecette2.recette2"
    :date="this.testposterecette2.date2"
    :heure="this.testposterecette2.heure2"
    :nblike="this.testposterecette2.nblike2"
    :nbcom="this.testposterecette2.nbcom2"
    :id="this.testposterecette2.id2"
    />
    <PostRecette 
    :auteur="this.auteur3" 
    :titre="this.testposterecette3.titre3"
    :recette="this.testposterecette3.recette3"
    :date="this.testposterecette3.date3"
    :heure="this.testposterecette3.heure3"
    :nblike="this.testposterecette3.nblike3"
    :nbcom="this.testposterecette3.nbcom3"
    :id="this.testposterecette3.id3"
    />
    
</template>