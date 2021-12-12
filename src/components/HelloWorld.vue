<template>
  <div>
    <!--<h1>Test</h1>
<button v-on:click="show = !show">Permutter</button>
  <transition name="fade">
    <p v-if="show">bonjour</p>
  </transition>
  <p>
        <img alt="" src="https://static.onzemondial.com/photo_article/723735/284173/1200-L-manchester-united-le-show-cristiano-ronaldo-relance-un-clash-evra-rgle-ses-comptes.jpg" 
            style="height: 85px; width: 198px" id="imgClickAndChange" v-on:click="changeImage()"  />
</p>-->

<img alt="" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/2560px-International_Pok%C3%A9mon_logo.svg.png" style="height: 400px">
<h1>Inscrit un nombre</h1>
  <input type="number" id="inputPoke" v-on:change="apiPoke">

<div id="exercice_4">
  <div class="block_image">
    <img alt="" src="" id="imgPokemon" style="height: 300px; width: 200px"/>
  </div>
  <div class="block_information">
    <h2>Informations</h2><br>
    <p><b>Id : </b> {{ this.idPoke }}</p>
    <p><b>Nom : </b>{{ this.nomPoke }}</p>
    <p><b>Poids : </b>{{ this.poidsPoke }} kg</p>

    <ul>
    <li v-for="value in this.typepk" :key="value.type.name">
      {{value.type.name}}
    </li>
  </ul>



    </div>
  </div>
</div>



</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return{
    show : true, 
    info: null, 
    idPoke : null, 
    nomPoke : null, 
    imagePoke : null,
    poidsPoke : null, 
    items: [],
    typepk: []

    }
  },
  
 methods: {
    logg: function () {
      console.log("press")
    }, 
    changeImage: function() {
      if (document.getElementById("imgClickAndChange").src == "https://static.onzemondial.com/photo_article/723735/284173/1200-L-manchester-united-le-show-cristiano-ronaldo-relance-un-clash-evra-rgle-ses-comptes.jpg") 
        {
            document.getElementById("imgClickAndChange").src = "https://static.onzemondial.com/photo_article/727033/285436/1200-L-psg-bruges-messi-tient-un-nouveau-chouchou-un-coup-de-nerfs-a-terni-la-soire.jpg";
        }
        else 
        {
            document.getElementById("imgClickAndChange").src = "https://static.onzemondial.com/photo_article/723735/284173/1200-L-manchester-united-le-show-cristiano-ronaldo-relance-un-clash-evra-rgle-ses-comptes.jpg";
        }
    }, 

 
apiPoke: function (){
  var i = document.getElementById('inputPoke').value
  var url = "https://pokeapi.co/api/v2/pokemon/" + i
  axios
      .get(url)
      .then(response => {this.info = response
      this.idPoke = response.data.id
      this.nomPoke = response.data.name
      this.poidsPoke = response.data.weight
      this.imagePoke = document.getElementById("imgPokemon").src = "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/" + this.idPoke + ".png";})
      this.typepk = response.data.types
      
     
      console.log(url)
      console.log(this.imagePoke)
      console.log(this.typepk)
      

  
  
},


  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

#exercice_4{
margin-top: 100px;
display: flex;
justify-content: center; 
}

.block_image{
  height: 300px;
  width: 200px;
  border-radius: 10%;
  border : solid black; 
  margin-right: 75px;
}

.block_information{
  height: 300px;
  width: 200px;
  border-radius: 10%;
  border : solid black; 
  margin-left: 75px;
}
</style>

