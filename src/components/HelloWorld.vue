<template>
  <div class="qrcode">
    <div class="headerofqrcode">
      <hr class="underline"> 
      <h1>{{title}}</h1>
        <div class="steps">
              <div class="dud">
                <p class="nbretape" v-on:click="num=0">1</p>
                <p>en-tete</p>
              </div>
              <div class="dud">
                <p class="nbretape" v-on:click="num=1">2</p>
                <p>corps</p>
              </div>
              <div class="dud">
                <p class="nbretape" v-on:click="num=2">3</p>
                <p>Pied de page</p>
              </div>
              <div class="dud">
                <p class="nbretape" >4</p>
                <p>creation terminé</p>
              </div>
        </div>
        <div class="qrcodeparm">
              <div class="topofqrcode" v-if="num==0">
                <div class="entete">
                  <label >importez le logo de votre en-tete</label><br><br>
                  <input type="file" id="logodentete" ><br><br><br>
                  <label >coisisez la couleur de votre en-tete</label><br><br>
                  <input type="color" v-model="entetecoul" id="couleurdentete" ><br><br><br>
                  <label >texte de l'en-tete</label><br><br>
                  <input type="text" v-model="qrheadtext" placeholder="entrez le texte de votre en-tete" class="textofheader">
                </div>
              </div>
 
              <div class="contenu" v-if="num==1">
                <div class="settings">
                  
                  <div class="textedelacarte">
                    <p>texte</p>
                    <input class="textscan" type="text" v-model="message" placeholder="entrez votre texte">
                  </div>
                  <div class="lesoptions">
                    <select name="SO" id="selectoption">
                      <option class="uneoption" value="1">options d'image</option>
                      <option class="uneoption"  value="2">options des points (style,couleurs)</option>
                      <option class="uneoption"  value="3">options des angles</option>
                    </select>
                  </div>
                  <div class="parametresbox">
                    <div id="parametreimage">

                    </div>
                    <div id="parametrespoints">
                      <div id="styledepoint">
                        <p>style de points</p>
                        <div class="genn">
                          <div id="inn1" class="inn">
                            <input v-model="cbarrondi.checked" value="." type="radio" name="cbarrondi"  >
                            <p>arrondi </p>
                          </div>
                          <div id="inn2" class="inn">
                            <input  v-model="cbcarre.checked"  type="radio" value="." name="cbarrondi22"  >
                            <p>carré </p>
                          </div>
                        </div>
                      </div>
                      <div id="type de couleur">
                        <p>type de couleur</p>
                        <div class="gann">
                          <div id="ann1" class="ann">
                            <input v-model="cbunique.checked" value="," type="radio" name="cbunique"  >
                            <p>Unique</p>
                          </div>
                          <div id="ann2" class="ann">
                            <input v-model="cbdegrade.checked" value="," type="radio" name="cbdegrade"  >
                            <p>degradé</p>
                          </div>
                          
                        </div>
                      </div>
                      <div id="choixdecouleur">
                        <p>couleur </p>
                        <input v-model="couleur" type="color" id="choixcouleur">

                      </div>
                    </div>
                    
                  </div>
                </div>
              </div>
              <div class="piedsdepage" v-if="num==2">
                  <div>
                    <label>ecrivez votre nom complet </label><br><br>
                    <input type="text" v-model="namecr"  class="copyrightname" placeholder="entrez votre nom compplet ici">
                  </div>
                  <br><br><br>
                  <div>
                    <label>créez votre tag personalisé</label><br><br>
                    <input type="text" v-model="tagcr" class="copyrighttag" pattern="[A-Z]{3}" placeholder="créez votre tag (example: #0000)">
                    
                  </div>
              </div>
              <div class="done" v-if="num==3">
                <h2 >votre carte QR code a été crée avec succées</h2>
              </div>
            </div>
    </div>
    
    <div>
      
      <div  :style="`background:${couleur}`" class="bigmama">
        <div class="bigmamacontent">
          <div :style="`background:${entetecoul}`" class="enteteqrc">
            <img src="" alt="">
            <label >{{qrheadtext}}</label>
          </div>
          <div class="bodyqrc">
            <img class="logobigmama" src="./../assets/5a354eb2b27245.7518178615134429947309.png" alt="">
            <img class="imgqrcode"  src="./../assets/qrcodeimg.png" alt="">  <br>
            <label class="textqrcode" >{{message}}</label>
          </div>
          <div class="footerqrc">
              <p>&copy; {{namecr}} {{tagcr}}</p>
          </div>
        </div>
        
    </div>
    <div class="lesbouttons">
        <button id="imprimer" class="bouttons">imprimer {{num}}</button>
        <button id="enregistrer" @click="num=3" class="bouttons">enregistrer</button>
    </div>
    </div>
  </div>
  
</template>

<script>

export default {
  // name: 'HelloWorld',
  props: {
    
  },
   data(){
    return {
      title:"personalisez votre QR code",
      message:'',
      couleur:'',
      entetecoul:'',
      qrheadtext:'',
      num:0,
      namecr:'',
      tagcr:'',
      
      cbarrondi:{
        checked:"on"
      },
      cbcarre:{
        checked:""
      },
      cbunique:{
        checked:'on'
      },
      cbdegrade:{
        checked:""
      },
      }
    },
    computed:{
      
    },
    watch:{
      "cbcarre.checked":function (newval ){
        if(newval=="."){
          this.cbarrondi.checked="";
        }else{
          this.cbarrondi.checked=".";
        }
      },
      "cbarrondi.checked":function ( newval){
        if(newval=="."){
          this.cbcarre.checked="";
        }else{
          this.cbcarre.checked=".";
        }
      },

      "cbunique.checked":function (newval ){
        if(newval==","){
          this.cbarrondi.checked="";
        }else{
          this.cbarrondi.checked=",";
        }
      },
      "cbdegrade.checked":function ( newval){
        if(newval==","){
          this.cbcarre.checked="";
        }else{
          this.cbcarre.checked=",";
        }
      }
    },
    methods(){
      
      
    },
    components(){
     
    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.done{
  border: solid;
  width: 450px;
  margin-top: 150px;
  
}
.footerqrc{
  margin-top: 110px;
    margin-left: 10px;
}
.copyrightname{
  width: 520px;
  height: 40px;
}
.copyrighttag{
  width: 520px;
  height: 40px;
}
.enteteqrc{
  width: 120%;
  height: 170px;
  right: 10%;
  position:relative;
  background-color: blueviolet;
 transform: rotate(-15deg);
  overflow: hidden;
 bottom: 55px;
}
.textofheader{
  width: 450px;
  height: 50px;
}
#couleurdentete{
  width: 300px;

}
#imprimer{
  margin-left: 140px;
}
#enregistrer{
  background-color: black;
  color: white;
}
.lesboutons{
  margin-left: 50px;
}
.bouttons{
  width: 120px;
  height: 35px;
  margin-right: 25px;
  margin-top: 20px;
}
.steps{
  display: flex;
  justify-content: space-between ;
}
.nbretape{
    height: 30px;
    width: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 22px;
    border: 3px solid red;
    color: red;
    background-color: white;
}
.nbretape:hover{
  background-color: red;
  color: aliceblue;
  cursor:pointer;
}
h1{
  display: flex;
  justify-content: top center;
 
}
.dud{
  padding-right: 100px;
  
}
.bigmama{
  background-color: goldenrod;
  height: 550px;
  width: 420px;
  margin-left: 50px;
  margin-top: 120px;
  justify-content: space-between;
  display: flex;
  flex-direction: column ;
}
.contenu{
  display: flex;
  position:relative;
}
.textscan{
  width: 580px;
  height: 50px;
}
#selectoption{
  margin-top: 50px;
  width: 580px;
  height: 50px;
}
.logobigmama{
  height: 90px;
  margin-left: 150px;
  margin-top: -50px;
}
.imgqrcode{
  height: 150px;
  margin-left: 130px;
  margin-top: 25px;
}
.underline{
  width: 440px;
  position: absolute;
  margin-top: 120px;
}
.qrcode{
  position: relative;
  display: flex;
  
}
.parmetresbox{
  border-style: solid;
  color:black ;
  height: 350px;
  width: 580px;
}
.genn{
  display: flex;
}
.inn{
  display: flex;
  align-items: center;
}
.gann{
  display: flex;
}
.ann{
  display: flex;
  align-items: center;
}
#inn1{
  margin-left: 25px;
}
#inn2{
  margin-left: 100px;
}
#ann1{
  margin-left: 25px;
}
#ann2{
  margin-left: 100px;
}
.qrcodeparm{
  width: 600px;
}
.lesoptions{
  margin-bottom: 100px;
}

#choixcouleur{
  width: 300px;
}
.qrcodetext{
  margin-left: 170px;
  
}
.textqrcode{
  margin-left: 170px;
  width: 100px;
  text-align: center;
}
.headerofqrcode{
  position: relative;
}
.bigmamacontent{
  overflow: hidden;
}

</style>
