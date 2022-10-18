<script>
export default{
    data(){
        return{
            lastName: "",
            firstName: "",
            email: "",
            age: "",
            message: "",
            userProfilList: [],
        }
    },
    methods: {
        modifyProfile: function () {
            let token = (localStorage.getItem("tokenUserLog"));
            const options = {
                method: "get",
                headers: {
                    "Content-Type": "application/json",
                    "Authorization": `bearer ${token}`,
                },
            }
        }
    }
}
const response = await fetch('https://social-network-api.osc-fr1.scalingo.io/foodbook/user, options')
const data = await response.json()
console.log('data:', data)


</script>



<template>
    <div class="formProfil">
        <h1>Votre Profil</h1>


        <button>Modifier son Profil</button>
        <form action="" class="form">
            <label for="nom">Entrez votre nom: <input type="text" placeholder="nom" v-model="this.lastName"></label>
            <label for="prénom">Entrez votre prénom: <input type="text" placeholder="prénom" v-model="this.firstName"></label>
            <label for="mail">Entrez votre mail: <input type="text" placeholder="mail" v-model="this.email"></label>
            <label for="pseudo">Entrez votre age: <input type="text" placeholder="age" v-model="this.age"></label>
            <input type="submit" value="valider">
        </form>
    </div>
</template>

<style lang="scss" scoped>

.formProfil{
    text-align: center;
    background-color: lightgray;
    .form{
    display: flex;
    flex-direction: column;
    align-items: center;
    align-content: space-between;
    text-align: center;
    input{
        margin-bottom: 20px;
    }
    
    
    }
}
</style>