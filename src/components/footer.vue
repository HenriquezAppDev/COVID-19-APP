<template>
  <div id="footer">
      <div class="container">
          <div class="row">
              <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6 col-xl-6">
                  <div class="col-12" id="links">
                      <p>Desarrollado por <a href="https://instagram.com/henriquezappdev"> HenriquezAppDev</a></p>
                      <p>Mapa COVID-19 Desarrollado por <a href="mailto:mapcovid19@gmail.com"> Fernando Caballero</a></p>
                      <p>API JSON Desarrollado por  <a href="https://mathdro.id/"> MathDroid</a></p>
                      <p>La fuente de todos los datos reflejados en este website son oficiales y provienen de la <a href="https://who.int/es/"> OMS</a></p>
                  </div>
              </div>
              <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6 col-xl-6">
                  <div class="col-12" id="logoHAD">
                      <img src="../assets/img/henriquezappdev.png" alt="HenriquezAppDev">
                  </div>

              </div>
          </div>                    
      </div>
  </div>
</template>

<script>
export default {
    name:'footerApp'
}
</script>

<style>
#footer{
    padding: 5% 0;
    border-top: 2px solid rgb(175, 175, 175);
    background: #000;
}
#logoHAD{
    text-align: center;    
    margin: 5% 0;
}
#logoHAD img{
    width: 60%;
}
#links p{
    color: #fff;
    font-weight: 300;
}
#links a{
    font-weight: 600;
    color: #a0a0a0;
    text-decoration: none;
}
</style>