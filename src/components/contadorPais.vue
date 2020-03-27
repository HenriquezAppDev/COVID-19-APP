<template>
    <div id="contadorPais">     
        <div class="container">
           <div class="row" id="selectPais">
              <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">
                <div class="col-12">
                <h4>Selecciona tu país:</h4>
                  <select v-model="selectPais" @change="getDataSelect(selectPais.iso)">                                    
                    <option  v-for="pais in arrPaises" v-bind:key="pais.nombrePais" v-bind:value="pais">
                      {{pais.nombrePais}}
                    </option>
                  </select>
                </div>
              </div>
           </div>
          <div class="row">            
            <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12 titulos">
                <h1>CORONAVIRUS</h1>                              
                <h3>CASOS DE COVID-19 EN {{selectPais.nombrePais}}</h3>           
            </div>
          </div>
          <div class="row" id="data_pais">
            <div class="col-xs-12 col-sm-12 col-md-12 col-lg-3 col-xl-3">
              <div class="col-12 item_data" id="confirmados_pais">
                  <h1>Confirmados</h1>
                  <h2>{{casosConfirmados | currency}}</h2>
              </div>
            </div>
            <div class="col-xs-12 col-sm-12 col-md-12 col-lg-3 col-xl-3">
              <div class="col-12 item_data" id="activos_pais">
                  <h1>Activos</h1>
                  <h2>{{casosActivos | currency}}</h2>
              </div>
            </div>
            <div class="col-xs-12 col-sm-12 col-md-12 col-lg-3 col-xl-3">
              <div class="col-12 item_data" id="recuperados_pais">
                  <h1>Recuperados</h1>
                  <h2>{{casosRecuperados | currency}}</h2>
              </div>
            </div>
            <div class="col-xs-12 col-sm-12 col-md-12 col-lg-3 col-xl-3">
              <div class="col-12 item_data" id="muertos_pais">
                  <h1>Muertos</h1>
                  <h2>{{casosMuertos | currency}}</h2>
              </div>
            </div>
          </div>
          <div class="row" id="updateFecha">
            <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">                                          
                <h3>Ultima actualización:</h3>           
                <h4>{{updateFecha | moment("DD/MM/YYYY  h:mm:ss A") }}</h4>
            </div>
          </div>
          <div class="row" id="compartir">        
            <div class="col-12">
              <div class="sharethis-inline-share-buttons"></div>
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

Vue.use(require('vue-moment'));


//Importando separador de miles 
import VueCurrencyFilter from 'vue-currency-filter'
//Dando uso al separador
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
    name: 'contadorPais',

    data(){
      return {
          casosActivos: null,
          casosConfirmados: null,
          casosRecuperados: null,
          casosMuertos: null,
          updateFecha: null,
          selectPais: "VE",
          arrPaises: [            
            {nombrePais:"VENEZUELA", iso:"VEN"},
            {nombrePais:"ARGENTINA", iso:"ARG"},
            {nombrePais:"ALEMANIA", iso:"DEU"},
            {nombrePais:"BRASIL", iso:"BRA"},
            {nombrePais:"BOLIVIA", iso:"BOL"},
            {nombrePais:"CANADA", iso:"CAN"},
            {nombrePais:"COLOMBIA", iso:"COL"},
            {nombrePais:"COSTA RICA", iso:"CRI"},
            {nombrePais:"CHILE", iso:"CHL"},
            {nombrePais:"CHINA", iso:"CHN"},
            {nombrePais:"CUBA", iso:"CUB"},
            {nombrePais:"GUATEMALA", iso:"GTM"},
            {nombrePais:"EL SALVADOR", iso:"SLV"},
            {nombrePais:"ECUADOR", iso:"ECU"},
            {nombrePais:"ESTADOS UNIDOS", iso:"USA"},
            {nombrePais:"ESPAÑA", iso:"ESP"},
            {nombrePais:"FRANCIA", iso:"FRA"},
            {nombrePais:"HONDURAS", iso:"HND"},
            {nombrePais:"ISRAEL", iso:"ISR"},
            {nombrePais:"ITALIA", iso:"ITA"},
            {nombrePais:"JAPÓN", iso:"JPN"},
            {nombrePais:"MEXICO", iso:"MEX"},
            {nombrePais:"NICARAGUA", iso:"NIC"},
            {nombrePais:"PAISES BAJOS", iso:"NLD"},
            {nombrePais:"PANAMA", iso:"PAN"},
            {nombrePais:"PARAGUAY", iso:"PRY"},
            {nombrePais:"PORTUGAL", iso:"PRT"},
            {nombrePais:"PUERTO RICO", iso:"PRI"},
            {nombrePais:"PERU", iso:"PER"},
            {nombrePais:"REP. DOMINICANA", iso:"DOM"},
            {nombrePais:"URUGUAY", iso:"URY"},
          ]

      }
    },
    mounted(){
      this.getDataPais("ve");
    },
    methods:{
      getDataPais(pais){
        Axios
          .get("https://covid19.mathdro.id/api/countries/"+pais)
            .then( res => {                
                this.casosConfirmados = res.data.confirmed.value;
                this.casosRecuperados = res.data.recovered.value;
                this.casosMuertos = res.data.deaths.value;
                this.updateFecha = res.data.lastUpdate
                this.casosActivos = this.casosConfirmados - this.casosRecuperados - this.casosMuertos;
                this.selectPais = this.arrPaises[0]
            })
            .catch( err => {
                console.log(err)
            })
      },
      getDataSelect: function(pais){        
        Axios
          .get("https://covid19.mathdro.id/api/countries/"+pais)
            .then( res => {                
                this.casosConfirmados = res.data.confirmed.value;
                this.casosRecuperados = res.data.recovered.value;
                this.casosMuertos = res.data.deaths.value;
                this.casosActivos = this.casosConfirmados - this.casosRecuperados - this.casosMuertos;
                this.updateFecha = res.data.lastUpdate
            })
            .catch( err => {
                console.log(err)
            })
      }
    }    
};
</script>

<style>
#contadorPais{
  padding-top: 2.5%; 
  color: #fff;
  padding-bottom: 5%;
  width: 100%;
  background: #222831;  
  background-image: url('../../src/assets/img/back3.jpg');
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: cover;
  box-shadow: 0px 1px 10px 0px rgba(0, 0, 0, 0.80);

}
#data_pais{  
  margin: 3% 0;
}
#contadorPais .titulos{  
  width: 100%;
  text-align: center;
  margin: 2% 0;
}
#contadorPais .titulos h1{
  font-size: 65px;
  font-weight: 800;
  color: #fff;
  text-shadow:  5px 4px 0px rgba(0,0,0,0.15);
  letter-spacing: -4px;
}
#contadorPais .titulos h3{
  font-size: 25px;
  font-weight: 300;
  letter-spacing: 3px;
}
.item_data{
  padding: 3% 0;
  text-align: center;
  border-radius: none;
  margin: 2% 0;  
}
.item_data h1{
  font-weight: 600;
  letter-spacing: -2px;  
  font-size: 30px;
  text-transform: uppercase;
  
}
.item_data h2{
  width: 100%;
  font-weight: 800;
  letter-spacing: -2px;
  font-size: 75px;
  margin: 15% 0;
  text-shadow:  5px 4px 0px rgba(0,0,0,0.15);
}
#muertos_pais h2{
  color: #ff004d;
}
#recuperados_pais h2{
  color: #4bd129;
}
#confirmados_pais h2{
  color: #ec9e00;
}
#activos_pais h2{
  color: #46b5d1;
}
#updateFecha{
    text-align: center;
    margin-bottom: 2%;
}
#updateFecha h3{
    font-size: 20px;
}
#selectPais{
  text-align: center;
  width: 100%;
}
#selectPais h4{
  color: #fff;
  font-weight: 300;
  letter-spacing: -1px;
  font-size: 20px;
}
#selectPais select{
  background: none;
  padding: .5% 3%;
  border-radius: 0 !important;
  color: #fff;
  font-weight: 600;
  font-size: 14px;
  text-align: center;
}
#selectPais option{
  text-align: center;
  font-weight: 600;
  color: #000;
  background: none;
}
#selectPais select:focus{
  outline: none !important;
}
#compartir{
  color: #fff;
}

.st-label, .st-shares{
  color: #fff !important;
}
.st-btn .st-label{
  color: initial !important;
}
@media (max-width: 425px) {
  #contadorPais .titulos h1 {
    font-size: 35px;
  }
  #contadorPais .titulos h3 {
    font-size: 25px;
  }
  #selectPais{
    margin: 5% 0;
  }
}
</style>