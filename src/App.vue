<template>
  <header class="mainBox">
      <div>
          <router-link :to="{ name: 'PokemonList'}" src="./assets/img/pokedex.png" class="logoPath" href="#">
            <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/25.png" style="width:50px; height:60px; vertical-align: middle;" alt="Pikachu">
          </router-link>
      <div>
      </div>
    </div>
      
  </header>
  <main>
        <router-view></router-view>
  </main>

</template>


<style lang="scss">

  .mainBox {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-top:15px; 

  

    @media (min-width: 300px) and (max-width: 439px){
    .pokedexLogo{
      width: 220px;
    }
  }
  }

  


</style>
