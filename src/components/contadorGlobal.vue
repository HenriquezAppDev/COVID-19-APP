<template>
    <div id="contadorGlobal">
       <div class="container">
           <div class="row mr-auto">
               <div class="col-12 titulos" >
                   <h1>Casos Globales</h1>
                   <hr class="myHR">
                   <div id="updateFecha">
                        <h3>Ultima actualización:</h3>           
                        <h4>{{updateFecha | moment("DD/MM/YYYY  h:mm:ss A") }}</h4>
                   </div>
               </div>
               <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3 col-xl-3">
                   <div class="col-12">
                       <div class="card">
                            <img class="card-img-top" src="../assets/img/confirmadosGlobal.jpg">
                            <div class="card-body" id="casosConfirmados">
                                <h5>Confirmados</h5>
                                <hr class="myHR">
                                <h1>{{casosConfirmados | currency }}</h1>                                
                            </div>
                        </div>
                   </div>
               </div>
               <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3 col-xl-3">
                   <div class="col-12">
                       <div class="card">
                            <img class="card-img-top" src="../assets/img/activosGlobal.jpg">
                            <div class="card-body" id="casosActivos">
                                <h5>Activos</h5>
                                <hr class="myHR">
                                <h1>{{casosActivos | currency }}</h1>                                
                            </div>
                        </div>
                   </div>
               </div>
               <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3 col-xl-3">
                   <div class="col-12">
                       <div class="card">
                            <img class="card-img-top" src="../assets/img/recuperadosGlobal.jpg">
                            <div class="card-body" id="casosRecuperados">
                                <h5>Recuperados</h5>
                                <hr class="myHR">
                                <h1>{{casosRecuperados | currency }}</h1>                                
                            </div>
                        </div>
                   </div>
               </div>
               <div class="col-xs-12 col-sm-12 col-md-6 col-lg-3 col-xl-3">
                   <div class="col-12">
                       <div class="card">
                            <img class="card-img-top" src="../assets/img/muertosGlobal.jpg">
                            <div class="card-body" id="casosMuertos" >
                                <h5>Muertos</h5>
                                <hr class="myHR">
                                <h1>{{casosMuertos | currency }}</h1>                                
                            </div>
                        </div>
                   </div>
               </div>
           </div>
       </div>
    </div>
</template>

<script>

//Importación Axios para Conectar con API
import Vue from 'vue';
import Axios from 'axios';
//Dando uso a variables definidas
Vue.use(Axios)

//Importando separador de miles 
import VueCurrencyFilter from 'vue-currency-filter'
//Dando uso al separador

Vue.use(require('vue-moment'));

Vue.use(VueCurrencyFilter,
{
  symbol : '',
  thousandsSeparator: '.',
  fractionCount: 0,
  fractionSeparator: ',',
  symbolPosition: 'front',
  symbolSpacing: true
});
export default {
    name: 'contadorGlobal',

    data(){
      return {
          casosActivos: null,
          casosConfirmados: null,
          casosRecuperados: null,
          casosMuertos: null,
          updateFecha: null
      }
    },
    mounted(){
      this.getDataGlobal();
    },
    methods:{
      getDataGlobal(){
        Axios
          .get("https://covid19.mathdro.id/api")
            .then( res => {                
                this.casosConfirmados = res.data.confirmed.value;
                this.casosRecuperados = res.data.recovered.value;
                this.casosMuertos = res.data.deaths.value;
                this.updateFecha = res.data.lastUpdate;
                this.casosActivos = this.casosConfirmados - this.casosRecuperados - this.casosMuertos;
            })
            .catch( err => {
                console.log(err)
            })
      }
    }    
};
</script>

<style>
#contadorGlobal{
    padding: 2.5% 0;
    text-align: center;
    background: #222831;    
    color: #fff;
}
#contadorGlobal .titulos h1{
    font-weight: 800;
    letter-spacing: -4px;    
    font-size: 50px;
    color: #fff;
}
#contadorGlobal .myHR{
    
    background: #fff;
    margin: 2% auto;
    height: 0.5px;
    width: 50%;
}
.card{
    width: 100%;
    margin: 5% 0;
    border: none !important;
    box-shadow: 0px 10px 11px -4px rgba(0,0,0,0.50);
}
.card .myHR{
    background: #fff !important;    
}
.card h5{
    font-size: 25px;
    font-weight: 300;
}
.card h1{
    margin: 2% 0;
    font-size: 40px;
    font-weight: 700;            
}
.card, .card-img-top, .card-body{    
    border-radius: 0;
}
.card #casosConfirmados{
    background: #ec9e00;
    color: #fff;
}
.card #casosRecuperados{
    background: #4bd129;    
    color: #fff
}
.card #casosMuertos{
    background: #ff004d;
    color: #fff;
}
.card #casosActivos{
    background: #46b5d1;
    color: #fff;
}

</style>