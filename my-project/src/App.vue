<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <region></region>
    <departement></departement>
    <commune></commune>
    
   
  
  </div>
</template>

<script>
// on va chercher les .vue que l'on veu afficher
import Region from './Region'
import Departement from './Departement'
import Commune from './Commune'

export default {
  name: 'app',
  data () {
    return {
      msg: 'first app GEO with VUE.js'
    }
  },
  components: { Region,
                Departement,     //le component rapelle toutes le svue que l'on a besoin
                Commune
               }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  /* display: inline-block; */
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
