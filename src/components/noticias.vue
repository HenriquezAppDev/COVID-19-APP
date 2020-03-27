<template>
  <div id="noticias">
      <div class="container">
          <div class="row">
              <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <div class="col-12 titulos">
                      <h1>Noticias</h1>
                      <hr class="myHR">
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'noticias'
}
</script>

<style>
#noticias{
    padding: 3% 0;
    background: #222831;
    text-align: center;
}
#noticias .titulos h1{
    font-weight: 800;
    letter-spacing: -4px;    
    font-size: 50px;
    color: #fff;
}
#noticias .myHR{
    
    background: #fff;
    margin: 2% auto;
    height: 0.5px;
    width: 50%;
}
</style>