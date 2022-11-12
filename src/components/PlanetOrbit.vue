<template>
  <div id="canvasDiv" class="flex flex-row-reverse place-items-center overflow-hidden z-50" style="background:#242424;min-height: 100vh;">

    <div class="w-full"><h1> Insert Content here</h1>
       </div>
  </div>
  
</template>
<script>
import {
  Scene,
  PerspectiveCamera,
  WebGLRenderer,
  TextureLoader,
  PlaneGeometry,
  MeshPhongMaterial,
  Mesh,
  PointLight,
  Color,
  Vector3,
  BufferGeometry,
  Float32BufferAttribute,
  PointsMaterial,
  AdditiveBlending,
  Points,
  Clock
} from 'three'
import { OrbitControls } from 'https://cdn.skypack.dev/three@0.136.0/examples/jsm/controls/OrbitControls'

setTimeout(e => {
  let canvas = document.createElement('canvas')
  canvas.setAttribute('id', 'canvasMain')
    // canvas.style.borderRadius="10px"
  let canvasDiv = document.getElementById('canvasDiv')

  canvasDiv.append(canvas)
  let target = document.getElementById('canvasMain')

  // Setup scene leh camera leh renderer
  var scene = new Scene()
  var fieldOfView = 75
  var aspectRatio = window.innerWidth / window.innerHeight
  var nearPlane = 0.1
  var farPlane = 1000
  var camera = new PerspectiveCamera(
    fieldOfView,
    aspectRatio,
    nearPlane,
    farPlane
  )
  var renderer = new WebGLRenderer({ antialias: true, canvas: target })
  renderer.setSize(window.innerWidth / 2, window.innerHeight / 2)

  // body ah kan appen leh
  //   document.body.prepend(renderer.domElement)

  // textrue loader hmanging kan load image

  var texture = new TextureLoader().load('/shaiwavepng.png')
  // var material = new MeshLambertMaterial({
  //   map: loader.
  // });
  var geometry = new PlaneGeometry(17, 10 * 0.75)
  var material = new MeshPhongMaterial({
    map: texture,
    transparent: true,
    normalScale: 1
  })
  material.emissive.set(0x000000)
  material.shininess = 1

  var mesh = new Mesh(geometry, material)
  mesh.position.set(0, 0, 0)

  // sceneah kan add leh
  scene.add(mesh)
  var light = new PointLight(0xffffff, 2, 0)
  light.position.set(1, 1, 100)
  scene.add(light)
  scene.background = new Color(0x242424)
  camera.position.set(0, 4, 20)
  //   document.body.appendChild(renderer.domElement)
  window.addEventListener('resize', event => {
    camera.aspect = innerWidth / innerHeight
    camera.updateProjectionMatrix()
    renderer.setSize(innerWidth/2, innerHeight/2)
  })
  let controls = new OrbitControls(camera, renderer.domElement)
  controls.enableDamping = false
  controls.enablePan = false
  //   controls.enableZoom = false
  //   controls.enabelRotate = false
  controls.maxPolarAngle = Math.PI / 2

  controls.enabled = false

  let gu = {
    time: { value: 0 }
  }
  let sizes = []
  let shift = []
  let pushShift = () => {
    shift.push(
      Math.random() * Math.PI,
      Math.random() * Math.PI * 2,
      (Math.random() * 0.9 + 0.1) * Math.PI * 0.1,
      Math.random() * 0.9 + 0.1
    )
  }
  let pts = new Array(10000).fill().map(p => {
    sizes.push(Math.random() * 1.5 + 0.5)
    pushShift()
    return new Vector3()
      .randomDirection()
      .multiplyScalar(Math.random() * 0.5 + 9.5)
  })
  for (let i = 0; i < 15000; i++) {
    let r = 10,
      R = 40
    let rand = Math.pow(Math.random(), 1.5)
    let radius = Math.sqrt(R * R * rand + (1 - rand) * r * r)
    pts.push(
      new Vector3().setFromCylindricalCoords(
        radius,
        Math.random() * 2 * Math.PI,
        (Math.random() - 0.5) * 2
      )
    )
    sizes.push(Math.random() * 1.5 + 0.5)
    pushShift()
  }

  let g = new BufferGeometry().setFromPoints(pts)
  g.setAttribute('sizes', new Float32BufferAttribute(sizes, 1))
  g.setAttribute('shift', new Float32BufferAttribute(shift, 4))
  let m = new PointsMaterial({
    size: 0.15,
    transparent: true,
    depthTest: false,
    blending: AdditiveBlending,
    onBeforeCompile: shader => {
      shader.uniforms.time = gu.time
      shader.vertexShader = `
      uniform float time;
      attribute float sizes;
      attribute vec4 shift;
      varying vec3 vColor;
      ${shader.vertexShader}
    `
        .replace(`gl_PointSize = size;`, `gl_PointSize = size * sizes;`)
        .replace(
          `#include <color_vertex>`,
          `#include <color_vertex>
        float d = length(abs(position) / vec3(40., 10., 40));
        d = clamp(d, 0., 1.);
        vColor = mix(vec3(102., 223., 73.), vec3(0., 135., 319.), d) / 255.;
      `
        )
        .replace(
          `#include <begin_vertex>`,
          `#include <begin_vertex>
        float t = time;
        float moveT = mod(shift.x + shift.z * t, PI2);
        float moveS = mod(shift.y + shift.z * t, PI2);
        transformed += vec3(cos(moveS) * sin(moveT), cos(moveT), sin(moveS) * sin(moveT)) * shift.a;
      `
        )
   
      shader.fragmentShader = `
      varying vec3 vColor;
      ${shader.fragmentShader}
    `
        .replace(
          `#include <clipping_planes_fragment>`,
          `#include <clipping_planes_fragment>
        float d = length(gl_PointCoord.xy - 0.5);
        //if (d > 0.5) discard;
      `
        )
        .replace(
          `vec4 diffuseColor = vec4( diffuse, opacity );`,
          `vec4 diffuseColor = vec4( vColor, smoothstep(0.5, 0.1, d)/* * 0.5 + 0.5*/ );`
        )
      console.log(shader.fragmentShader)
    }
  })
  let p = new Points(g, m)
  p.rotation.order = 'ZYX'
  p.rotation.z = 0.2
  scene.add(p)

  let clock = new Clock()
  let arr = [0, 4, 20]
  let direction = 'forward'
  mesh.rotation.y = -5
      mesh.rotation.x = -5
  let meshRotationInt = 0
  renderer.setAnimationLoop(() => {

    if (direction == 'forward') {
      if (arr[2] > 18) arr[2] = arr[2] + 0.001
      if (arr[2] > 19) arr[2] = arr[2] + 0.0005
      else arr[2] = arr[2] + 0.01
      camera.position.set(0, 4, arr[2])
      meshRotationInt = meshRotationInt + 0.0001
      mesh.rotation.y = meshRotationInt
      mesh.rotation.x = meshRotationInt

      if (arr[2] > 20) {
        direction = 'notForward'
      }
    } else {
      meshRotationInt = meshRotationInt - 0.0001
      mesh.rotation.y = meshRotationInt
      mesh.rotation.x = meshRotationInt

      arr[2] = arr[2] - 0.01
      camera.position.set(0, 4, arr[2])
      if (arr[2] < 5) {
        direction = 'forward'
      }
    }
    // camera.position.set(0, 4, 20)
    controls.update()
    let t = clock.getElapsedTime() * 0.5
    gu.time.value = t * Math.PI
    p.rotation.y = t * 0.05
    renderer.render(scene, camera)
  })
  animate()
}, 1)
</script>
