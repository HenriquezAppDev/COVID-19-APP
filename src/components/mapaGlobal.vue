<template>
  <div id="mapaGlobal">
      <div class="container">
          <div class="row">
              <div class="col-12 titulos">
                  <h1 >Así se encuentra el mundo</h1>
                  <hr class="myHR">
              </div>
              <div class="col-xs-12 col-sm-12 col-md-10 col-lg-10 col-xl-10" id="mapa">
                  <div class="col-12" >
                      <iframe src="https://www.google.com/maps/d/embed?mid=1S0vCi3BA-7DOCS13MomK7KebkPsvYl8C" width="100%" height="480"></iframe>
                  </div>
              </div>
              
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'mapaGlobal'

}
</script>

<style>
#mapaGlobal{
    text-align: center;
    color: #fff;
    padding: 5% 0;
    background: #222831;    
}
#mapaGlobal iframe{
    border: 10px solid #fff;
}
#mapaGlobal #mapa{    
    margin: 0 auto;
}
#mapaGlobal p{
    font-size: 12px;
}
#mapaGlobal .titulos h1{
    font-weight: 800;
    letter-spacing: -4px;
    font-size: 50px;
    color: #fff;
}
#mapaGlobal .titulos .myHR{
    width: 50%;
    height: 1px;
    margin: 3% auto;
    background: #fff;
}


</style>