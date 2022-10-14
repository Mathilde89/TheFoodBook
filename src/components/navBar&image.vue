<template>
  <header>
    <div class="navBar">
      <nav>
        <img src="../src/img/logo.png">
        <RouterLink class="routerLink" to="/">Home</RouterLink>
        <RouterLink class="routerLink" to="/about">About</RouterLink>
        <RouterLink class="routerLink" to="/inscription">Inscription</RouterLink>
        <RouterLink class="routerLink" to="/connexion">Connexion</RouterLink>
      </nav>
    </div>
    
  </header>
  <div>
    <div class="image-main">
      <img src="../src/img/logo.png">
      <h1>VOTRE RESEAU SOCIAL CULINAIRE PREFERE</h1>
    </div>
  </div>

  <RouterView />
  <div class="cardContent">
    
  </div>
</template>