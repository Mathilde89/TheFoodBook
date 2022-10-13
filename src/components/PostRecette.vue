<script>
const PostRecette = {
    //Ici ce sont les données liés à un post
    props: ["auteur", "titre", "recette", "date", "heure", "nblike", "nbcom", "id",],
};
export default PostRecette;
// export default {
//     props: ["auteur", "titre", "recette", "date", "heure", "nblike", "nbcom", "id",],
//     methods: {
//         clikckCom: function(){
// //arret ici
//         }

//     },
// }
</script>

<template>
    <div class="post">

        <div class="tittle">
            {{titre}}

        </div>
        <div class="recette">
            <p>
                {{recette}}
            </p>

        </div>
        <div class="footerpost">
            <div class="like">
                <button class="buttonlike">
                    <i class="fa-solid fa-heart"></i>
                </button>
                <div class="nblike">
                    {{nblike}} <i class="fa-solid fa-heart"></i>
                </div>
            </div>
            <div class="com">
                <button class="buttoncom">
                    <i class="fa-solid fa-comments"></i>
                </button>
                <div class="nbcom">
                    {{nbcom}} commentaires
                </div>

            </div>

           

        </div>
        <div class="listcom">
                Liste com

            </div>
    </div>
</template>


<style lang="scss" scoped>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
}

$colorPrimary: #A52A2A;
$colorGreyLight: #D3D3D3;
$colorGreyMedium: #A9A9A9;
$colorGreyDark: #353535;
$taillewidhtpost:500px;

.post {
    width: $taillewidhtpost;
    height: 400px;
    background-color: $colorGreyLight;
    padding: 20px;
    margin: 20px;
    border-radius: 20px;
    box-shadow: rgba(17, 17, 26, 0.1) 0px 4px 16px, rgba(17, 17, 26, 0.05) 0px 8px 32px;
}

.tittle {
    color: $colorPrimary;
    height: 10%;
    width: 100%;
}

.recette {
    height: 80%;
    width: 100%;
    background-color: white;
    border-radius: 20px;

    p {
        padding: 10px;
    }

}

.footerpost {
    height: auto;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;

}

.com {
    height: 100%;
    width: 50%;
    display: flex;
    flex-direction: row;
    justify-content: center;
}

.like {
    height: 100%;
    width: 50%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;


}

button {
    width: 40px;
    height: 40px;
    margin: 10px;
    justify-content: flex-end;
    display: block;
    color: #fff;
    background: $colorGreyDark;
    font-size: 1em;
    font-weight: bold;
    outline: none;
    border: none;
    border-radius: 5px;
    transition: 0.2s ease-in;
    cursor: pointer;
}

.nblike {

    align-items: center;
    vertical-align: flex-start;
    width: 40%;
    color: $colorGreyDark;
}

.com {

    align-items: center;
    vertical-align: flex-start;
    width: 40%;
    color: $colorGreyDark;
}
.listcom{
    width: $taillewidhtpost;
    height: 200px;
    background-color: #A52A2A;
    padding: 20px;
    border-radius: 20px;


}
</style>