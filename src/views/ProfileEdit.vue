<script setup>
import PostRecette from '../components/PostRecette.vue';
</script>

<script>

export default{
    data() {
        lastName: "";
        return {
            userProfilList: {},
            listPost: [],
            array: "test"
        };
    },
    methods: {
        showPost: async function () {
            await this.getPosts();
            console.log("test");
            console.log(this.listPost);
        },
        getPosts: async function () {
            const options = {
                method: "GET",
                headers: {
                    "Content-Type": "application/json"
                },
            };
            const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/foodbook/posts?page=0&limit=10", options);
            const data = await response.json();
            this.listPost = data.posts;
            console.log("listpost", this.listPost);
            
        },
        modifyProfile: async function () {
            let token = JSON.parse(localStorage.getItem("tokenUserLog"));
            console.log(token);
            const options = {
                method: "GET",
                headers: {
                    "Content-Type": "application/json",
                    "Authorization": `bearer ${token}`,
                },
            };
            const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/foodbook/user", options);
            const data = await response.json();
            console.log("data:", data);
            console.log("userProfilList", this.userProfilList);
            this.userProfilList = data;
        },
        modifyInfoProfile: async function () {
            let token = JSON.parse(localStorage.getItem("tokenUserLog"));
            console.log(token);
            const options = {
                method: "PUT",
                headers: {
                    "Content-Type": "application/json",
                    "Authorization": `bearer ${token}`,
                },
                Body: JSON.stringify({
                    firstName: this.userProfilList.firstName,
                    lastName: this.userProfilList.lastName,
                    email: this.userProfilList.email,
                    age: this.userProfilList.age
                })
            };
            const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/foodbook/user", options);
            const data = await response.json();
            console.log("data:", data);
            this.result = data.success;
            console.log("userProfilList", this.userProfilList);
        },
    },
    
};



</script>



<template>
    <div class="formProfil">
        <h1>Votre Profil</h1>
        <form type="submit" @submit.prevent="modifyProfile()" @click="modifyProfile()">
            <button >afficher son Profil</button>
        </form>

        
        <form class="form" @submit.prevent="modifyInfoProfile()" >
            
            <label for="nom">Entrez votre nom:<input type="text" :placeholder="nom"  v-model="this.userProfilList.lastname"></label>
            <label for="prénom">Entrez votre prénom: <input type="text" :placeholder="prénom"  v-model="this.userProfilList.firstname"></label>
            <label for="mail">Entrez votre email: <input type="text" :placeholder="email" v-model="this.userProfilList.email"></label>
            <button>modifier son profil</button>
        </form>
    </div>
    <div class="UserPosts">
        <button @click="showPost">teeeest</button>
        <PostRecette
        :titre="array"
        />
    </div>
</template>

<style lang="scss" scoped>

.formProfil{
    display: flex;
    flex-direction: column;
    text-align: center;
    background-color: lightgray;
    justify-content: center;
    
    button{
        border-radius: 10px;
        background-color: rgb(7, 69, 2);
        color: white;
        margin-bottom: 20px;

    }
    .form{
    display: flex;
    flex-direction: column;
    align-items: center;
    align-content: space-between;
    text-align: center;
    justify-content: center;
    input{
        display: flex;
        margin-bottom: 20px;
        justify-content: center;
    }
    
    
    }
}
</style>