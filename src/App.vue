<template>
  <div id="app">
    <contador-pais/>
    <headquote/>
    <contador-global/>
    <mapa-global/>
    <fuentes-oficiales/>
    <footer-app/>
  </div> 
</template>

<script>
import contadorPais from './components/contadorPais.vue';
import contadorGlobal from './components/contadorGlobal.vue';
import mapaGlobal from './components/mapaGlobal.vue';
import footerApp from './components/footer.vue';
import headquote from './components/headquote.vue';
import fuentesOficiales from './components/fuentesOficiales.vue';

import Vue from 'vue'
import VueI18n from 'vue-i18n'

Vue.use(VueI18n)

export default {
  name: 'App',
  components: {
    contadorPais,
    contadorGlobal,
    mapaGlobal,
    footerApp,
    headquote, 
    fuentesOficiales
  }
}


</script>

<style>
#app{
  font-family: 'Open Sans', sans-serif;
}
</style>
