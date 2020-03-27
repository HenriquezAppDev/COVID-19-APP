<template>
  <div id="fuentesOficiales">
      <div class="container">
          <div class="row">
              <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <div class="col-12 titulos">
                      <h1>Fuentes Oficiales</h1>
                      <hr class="myHR">
                  </div>
              </div>
          </div>
          <div class="row" id="list">
              <div v-for="fuente in arrFuentes" v-bind:key="fuente.id" class="col-xs-12 col-sm-12 col-md-6 col-lg-4 col-xl-4">
                   <div class="col-12">
                       <div class="card">
                            <img class="card-img-top" v-bind:src="fuente.img">
                            <div class="card-body">
                                <h1>{{fuente.nombre}}</h1> 
                                <hr class="myHR">
                                <p>{{fuente.pais}}</p>
                                                                                         
                                <a v-bind:href="fuente.url" target="blank" class="myBTN">Website</a>
                            </div>
                        </div>
                   </div>
               </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name:'fuentesOficiales',

    data(){
        return{
            arrFuentes: [
                {   pais: "Mundial",
                    nombre: "OMS", 
                    img:"https://firebasestorage.googleapis.com/v0/b/covid19-venezuela.appspot.com/o/oms.jpg?alt=media&token=a057fe09-eb91-4610-9741-1f53dc4c980e", 
                    url:"https://www.who.int/es/emergencies/diseases/novel-coronavirus-2019"
                },
                {   pais: "Mundial",
                    nombre: "ONU", 
                    img:"https://firebasestorage.googleapis.com/v0/b/covid19-venezuela.appspot.com/o/onu.jpg?alt=media&token=00f28706-e5e5-46bf-ac96-42add63ddaaf", 
                    url:"https://www.un.org/es/coronavirus"
                }
            ]
        }
    }
}
</script>

<style>
#fuentesOficiales{
    text-align: center;
    padding: 3% 0;
    background: #222831;    
    color: #fff;;
}
#fuentesOficiales .titulos h1{
    font-weight: 800;
    letter-spacing: -4px;    
    font-size: 50px;
    color: #fff;
}
#fuentesOficiales .myHR{
    
    background: #fff;
    margin: 2% auto;
    height: 0.5px;
    width: 50%;
}
#fuentesOficiales .card{
    background: #46b5d1;
}
#fuentesOficiales .card a{
    color: #46b5d1;
    font-weight: 600;
    text-decoration: none;
}
#fuentesOficiales .card p{
    text-transform: uppercase;
}
#fuentesOficiales .card h1{
    letter-spacing: -2px;
    font-size: 20px;
    font-weight: 600;
    text-align: center;
    color: #fff;
    margin: 5% auto;
}
.myBTN{
    padding: 3% 7%;
    background: #fff;    
}
#fuentesOficiales #list{
    justify-content: center;
}
</style>