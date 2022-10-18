<script>
export default{
    data(){
        return{
            userProfilList: {lastName: "", firstName: "", email: "", age: "", token:"",} 
        };
    },
    methods: {
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
            console.log('data:', data)
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
                Body:  JSON.stringify({
                    firstName: this.userProfilList.firstName,
                    lastName: this.userProfilList.lastName,
                    email: this.userProfilList.email,
                    age: this.userProfilList.age
                })
            };
            const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/foodbook/user", options);
            const data = await response.json();
            console.log('data:', data)
            this.result = data.success;
            console.log("userProfilList" , this.userProfilList);

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
            
            <label for="nom">Entrez votre nom:<input type="text" :placeholder=" `${this.userProfilList.valueOf(this.lastName)}`"  v-model="this.userProfilList.lastName"></label>
            <label for="prénom">Entrez votre prénom: <input type="text" :placeholder=" `${this.userProfilList.firstName}`"  v-model="this.userProfilList.firstName"></label>
            <label for="mail">Entrez votre mail: <input type="text" :placeholder="`${this.userProfilList.firstName}`" v-model="this.userProfilList.email"></label>
            <label for="pseudo">Entrez votre age: <input type="text" placeholder="age" v-model="this.userProfilList.age"></label>
            <input type="submit"  value="valider">
        </form>
    </div>
</template>

<style lang="scss" scoped>

.formProfil{
    display: flex;
    flex-direction: column;
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