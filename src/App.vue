<template>
  <div>

     <header>
       <div>
         <img class="icon1" src="./assets/5a354eb2b27245.7518178615134429947309.png" > 
       </div>
       <div>
         <img class="icon2" src="./assets/kisspng-money-bag-computer-icons-coin-clip-art-bag-money-icon-5ab0668e4e4f21.2772478315215100303208.png" alt="">
       </div>
       <div class="iconsbar">
          <div class="iconn">
            <i class="fa fa-search"></i>
          </div>
          <div class="iconn">
            <i class="fa fa-user"></i>
          </div>
          <div class="iconn">
            <i class="fa fa-bell-o" ></i>
          </div >
          <div id="langues">
            <div>
              <label for="">FR</label>
              <input  type="radio" id="radioFR">
            </div>
            <div>
              <label for="">EN</label>
              <input type="radio"  id="radioEN">
            </div>
          </div>
       </div>
     </header>
<hr class="horizontal">
    <div class="bodyofpage">
      <sidebar>
          <div>
            <h2>Dashboard</h2>
          </div>
          <div>
            <h2>restaurant</h2>
          </div>
          <div class="grp">
            <h2>menu</h2>
            <button :class="`btnopen ${openmenu?'active':''}`" v-on:click="openmenu= !openmenu ">
             <template v-if="openmenu">
              -
             </template>
             <template v-else>
              +
             </template>
              </button>
          </div>
          <div>
              <h3 v-if="openmenu"  :class="` ${openmenu?'active':''}`">Les menus</h3>
              <h3 v-if="openmenu"  :class="` ${openmenu?'active':''}`">Qr code </h3>
            </div>
          <div class="grp">
            <h2>reservations</h2>
            <button class="btnopen" v-on:click="openreservations= !openreservations">
              <template v-if="openreservations">
              -
             </template>
             <template v-else>
              +
             </template>
              </button>
          </div>
          <div>
              <h3 v-if="openreservations">hide</h3>
              <h3 v-if="openreservations">play</h3>
            </div>
          <div>
            <h2>Utilisateurs</h2>
          </div>
          <div>
            <h2>Rapport</h2>
          </div>
          <div class="grp">
            <h2>Parametres</h2>
            <button class="btnopen" v-on:click="openparametres= !openparametres">
              <template v-if="openparametres">
              -
             </template>
             <template v-else>
              +
             </template>
              </button>
          </div>
          <div>
              <h3 v-if="openparametres">cool</h3>
              <h3 v-if="openparametres">page</h3>
            </div>
      </sidebar>
      <hr class="verticale">
      <HelloWorld>
      </HelloWorld>
    </div>
  </div>
  
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: 'App',
  components: {
    HelloWorld:HelloWorld,
  },
  data(){
    return {
      openmenu:false,
      openreservations:false,
      openparametres:false,
      
    }
  },
  methods(){
    
  }
  
}


</script>

<style>

.icon1{
  height:85px;

}
.icon2{
  height: 85px;
}
header{
  
  position: relative;
  display: flex ;
  justify-content: space-between;

}
.iconsbar{
    display: flex;
    position: relative;
    border: 0cm;
    width: 220px;
    justify-content: space-between;
    align-items: center;
}
.grp{
  display: flex;
  align-items: center;
  

}
.btnopen{
    height: 22px;
    border-radius: 25px;
    width: 22px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 18px;
    background: transparent;
    border: 3px solid orange;
    color: orange;
}
.btnopen:hover{
  background-color: orange;
  color: black; 
  cursor:pointer;
}
sidebar{
  width: 200px;
  padding-left: 50px;
}
.bodyofpage{
  display: flex;
}
.verticale{
  margin-left: 0px;
  margin-top: 0px;
  margin-right: 120px;
  height: 800px;
}
.horizontal{
  width: 1255px;
  margin-right: 0px;
}

h3{
  color: orange;
}
</style>
