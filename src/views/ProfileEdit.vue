<template>
    <div class="formProfil">
        <h1>Votre Profil</h1>


        <h2>Modifier son Profil</h2>
        <form action="" class="form">
            <label for="nom">Entrez votre nom: <input type="text" placeholder="nom"></label>
            <label for="prénom">Entrez votre prénom: <input type="text" placeholder="prénom"></label>
            <label for="mail">Entrez votre mail: <input type="text" placeholder="mail"></label>
            <label for="pseudo">Entrez votre nom: <input type="text" placeholder="pseudo"></label>
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