<template>
  <div id="headquote">
      <div class="container">
        <div class="row">
            <div class="col-12">
                <div class="col-12">
                    <h1>#QuedateEnCasa</h1>                    
                    <h2>#StayAtHome</h2>
                </div>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'headquote'
}
</script>

<style>
#headquote{
    text-align: center;
    padding: 2% 0;
    width:100%;
    background: #ff004d;
    /* background: #d1cebd; */
}
#headquote h1{
    letter-spacing: -3px;
    color: #fff;
    font-weight: 800;
    text-shadow:  5px 4px 0px rgba(0,0,0,0.15);    
}
#headquote h2{
    font-weight: 300;
    color: #fff;    
    font-style: italic;
}
#headquote .myHR{
    width: 50%;
    background: #fff;
}
@media (max-width: 425px) {
  #headquote{
      padding: 5% 0;
  }  
  #headquote h1 {
    font-size: 35px;
  }
  #headquote h2 {
    font-size: 25px;
  }
}
</style>