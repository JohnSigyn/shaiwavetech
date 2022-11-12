<template>
  <!-- <div class="overflow-x-hidden stacking-slide">
    <Main />
    <div class="">
      <div class="">
        <AnimationOnScroll />
      </div>
    </div>
  </div> -->
  <div id="canvasId"></div>
</template>
<script setup></script>

<script>
import * as THREE from 'three'
import { OrbitControls } from 'https://cdn.skypack.dev/three@0.136.0/examples/jsm/controls/OrbitControls'
setTimeout(e => {


  // Setup scene leh camera leh renderer
var scene = new THREE.Scene();
var fieldOfView = 75;
var aspectRatio = window.innerWidth / window.innerHeight;
var nearPlane = 0.1;
var farPlane = 1000;
var camera = new THREE.PerspectiveCamera(
  fieldOfView, aspectRatio, nearPlane, farPlane
);
var renderer = new THREE.WebGLRenderer({antialias: true});
renderer.setSize( window.innerWidth, window.innerHeight );
 
// body ah kan appen leh
document.body.appendChild( renderer.domElement );


// textrue loader hmanging kan load image

var texture = new THREE.TextureLoader().load('/shaiwavepng.png')
// var material = new THREE.MeshLambertMaterial({
//   map: loader.
// });
var geometry = new THREE.PlaneGeometry(17, 10*.75);
var material = new THREE.MeshPhongMaterial({map: texture, transparent: true,normalScale:1});
material.emissive.set(0x000000);
material.shininess = 1;

var mesh = new THREE.Mesh(geometry, material);
mesh.position.set(0,0,0)


// sceneah kan add leh
scene.add(mesh);
var light = new THREE.PointLight( 0xffffff, 2, 0 );
light.position.set(1, 1, 100 );
scene.add(light)
scene.background = new THREE.Color(0x160016);
camera.position.set(0, 4, 21);
document.body.appendChild(renderer.domElement);
window.addEventListener("resize", event => {
  camera.aspect = innerWidth / innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(innerWidth, innerHeight);
})
let controls = new OrbitControls(camera, renderer.domElement);
controls.enableDamping = false;
controls.enablePan = false;
controls.enableZoom = false;
controls.enabelRotate = false;
controls.maxPolarAngle = Math.PI/2; 

controls.enabled = false




let gu = {
  time: {value: 0}
}
let sizes = [];
let shift = [];
let pushShift = () => {
  shift.push(
    Math.random() * Math.PI, 
    Math.random() * Math.PI * 2, 
    (Math.random() * 0.9 + 0.1) * Math.PI * 0.1,
    Math.random() * 0.9 + 0.1
  );
}
let pts = new Array(25000).fill().map(p => {
  sizes.push(Math.random() * 1.5 + 0.5);
  pushShift();
  return new THREE.Vector3().randomDirection().multiplyScalar(Math.random() * 0.5 + 9.5);
})
for(let i = 0; i < 50000; i++){
  let r = 10, R = 40;
  let rand = Math.pow(Math.random(), 1.5);
  let radius = Math.sqrt(R * R * rand + (1 - rand) * r * r);
  pts.push(new THREE.Vector3().setFromCylindricalCoords(radius, Math.random() * 2 * Math.PI, (Math.random() - 0.5) * 2 ));
  sizes.push(Math.random() * 1.5 + 0.5);
  pushShift();
}

let g = new THREE.BufferGeometry().setFromPoints(pts);
g.setAttribute("sizes", new THREE.Float32BufferAttribute(sizes, 1));
g.setAttribute("shift", new THREE.Float32BufferAttribute(shift, 4));
let m = new THREE.PointsMaterial({
  size: 0.15,
  transparent: true,
  depthTest: false,
  blending: THREE.AdditiveBlending,
  onBeforeCompile: shader => {
    shader.uniforms.time = gu.time;
    shader.vertexShader = `
      uniform float time;
      attribute float sizes;
      attribute vec4 shift;
      varying vec3 vColor;
      ${shader.vertexShader}
    `.replace(
      `gl_PointSize = size;`,
      `gl_PointSize = size * sizes;`
    ).replace(
      `#include <color_vertex>`,
      `#include <color_vertex>
        float d = length(abs(position) / vec3(40., 10., 40));
        d = clamp(d, 0., 1.);
        vColor = mix(vec3(227., 155., 0.), vec3(100., 50., 255.), d) / 255.;
      `
    ).replace(
      `#include <begin_vertex>`,
      `#include <begin_vertex>
        float t = time;
        float moveT = mod(shift.x + shift.z * t, PI2);
        float moveS = mod(shift.y + shift.z * t, PI2);
        transformed += vec3(cos(moveS) * sin(moveT), cos(moveT), sin(moveS) * sin(moveT)) * shift.a;
      `
    );
    console.log(shader.vertexShader);
    shader.fragmentShader = `
      varying vec3 vColor;
      ${shader.fragmentShader}
    `.replace(
      `#include <clipping_planes_fragment>`,
      `#include <clipping_planes_fragment>
        float d = length(gl_PointCoord.xy - 0.5);
        //if (d > 0.5) discard;
      `
    ).replace(
      `vec4 diffuseColor = vec4( diffuse, opacity );`,
      `vec4 diffuseColor = vec4( vColor, smoothstep(0.5, 0.1, d)/* * 0.5 + 0.5*/ );`
    );
    console.log(shader.fragmentShader);
  }
});
let p = new THREE.Points(g, m);
p.rotation.order = "ZYX";
p.rotation.z = 0.2;
scene.add(p)

let clock = new THREE.Clock();




  

  renderer.setAnimationLoop(() => {
    controls.update()
    let t = clock.getElapsedTime() * 0.5
    gu.time.value = t * Math.PI
    p.rotation.y = t * 0.05
    renderer.render(scene, camera)
  })
  animate()
}, 1)

import Main from '../src/components/Main.vue'
import AnimationOnScroll from '../src/components/AnimationOnScroll.vue'
import { ref } from '@vue/reactivity'
import { animate } from 'tsparticles-engine'

export default {
  components: {
    Main,
    AnimationOnScroll
  }
}
</script>
<style scoped>
.stacking-slide {
  width: 100%;
  position: sticky;
  top: 0;
}
</style>
