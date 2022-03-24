<style>
@import './assets/base.css';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


<template class="home">

  
  <div id="app">
    <div class="accueil">
      <h1>TEST</h1>
      <Accueil />
    </div>
    
    
  </div>
  
</template>

<script >

import Accueil from './components/Accueil.vue'

export default {
  name: 'Home',
  components: {
    Accueil,
  },
  data() {
    return {
      message: 'Accueil',
    }
  },
  
}

</script>


