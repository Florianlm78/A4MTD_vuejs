
<template>
  <div>
      <div id="container"></div>
      <button v-on:click="accelerer()">accelerer</button>
  </div>

</template>

<script>
import * as three from 'three'
export default {
    name:'TreeJS',
    data(){
        return{
            scene:null,
            camera:null,
            renderer:null,
            mesh:null,
        }
    },
     methods: {
    init: function() {
        let container = document.getElementById('container');
        this.camera = new three.PerspectiveCamera(70, container.clientWidth/container.clientHeight, 0.01, 20);
        this.camera.position.z = 15;
        this.camera.position.x = 0;
        this.camera.position.y = 0  ;

        this.scene = new three.Scene();
     

        const geometry = new three.PlaneGeometry( 10   , 10 );
        const terre = new three.MeshBasicMaterial( {color: 0x32CD32, side: three.DoubleSide} );
        this.mesh = new three.Mesh( geometry, terre )
         this.scene.add(this.mesh);
        this.mesh.position.x = 0
        this.mesh.position.y = 0
        this.renderer = new three.WebGLRenderer({antialias: true});
        this.renderer.setSize(container.clientWidth, container.clientHeight);
        container.appendChild(this.renderer.domElement);
},
    animate: function() {
        requestAnimationFrame(this.animate);
        this.mesh.rotation.x += 0.05;
        this.mesh.rotation.y += 0.02;
        this.renderer.render(this.scene, this.camera);
    },

    accelerer: function(){
        requestAnimationFrame(this.animate);
        this.mesh.rotation.x += 0.00;
        this.mesh.rotation.y += 0.00;
    },
    

    ralentir: function(){
        requestAnimationFrame(this.animate);
        this.mesh.rotation.x -= 0.05;
        this.mesh.rotation.y -= 0.02;
    }
    

  },
    mounted(){
        this.init();
        this.animate();
    },
     

}

</script>

<style>
#scene-container {
  width: 80%;
  height: 80%;
  background-color: skyblue;
}
#container{
    width: 1000px;
    height: 700px;
    margin-left: auto;
    margin-right: auto;
  }

</style>