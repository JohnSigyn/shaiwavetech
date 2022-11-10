<template>
  <div
    class="bg-slate-900 flex justify-center items-center overflow-hidden relative z-100"
    style="min-height:100vh;min-width:99.1vw;position:relative"
  >
  
    <Particles
        style="min-width:100vh;min-height:100vh !important;position:absolute"
      id="tsparticles" class="particles"
      :particlesInit="particlesInit"
      :particlesLoaded="particlesLoaded"
      :options="{
        background: {
          color: {
            value: 'none'
          }
        },
        style:{
            height:1366
        },
        fpsLimit: 120,
        interactivity: {
          events: {
            onClick: {
              enable: true,
              mode: 'push'
            },
            onHover: {
              enable: true,
              mode: 'repulse'
            },
            resize: true
          },
          modes: {
            bubble: {
              distance: 200,
              duration: 2,
              opacity: 0.8,
              size: 120
            },
            push: {
              quantity: 3
            },
            repulse: {
              distance: 20,
              duration: 0.4
            }
          }
        },
        particles: {
          color: {
            value: '#66df49'
          },
          links: {
            color: '#009bdb',
            distance: 180,
            enable: true,
            opacity: 0.5,
            width: 1
          },
          collisions: {
            enable: false
          },
          move: {
            direction: 'none',
            enable: true,
            outModes: {
              default: 'bounce'
            },
            random: false,
            speed: 2,
            straight: true
          },
          number: {
            density: {
              enable: true,
              area: 800
            },
            value: 60
          },
          opacity: {
            value: 0.5
          },
          shape: {
            type: 'circle'
          },
          size: {
            value: { min: 1, max: 5 }
          }
        },
        fullScreen:false,
        detectRetina: false
      }"
    />
    <div class="z-50 tracking-wide">
      <div class="flex justify-center mainTitle mb-5">
        <div><h1 class="title tracking-widest" style="font-size:10rem" >SHAI</h1></div>
        <div id="ui">
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
          <div class="text" style="color:#009bdb">WAVE</div>
        </div>
        <div>
        <h1 class="opacity-0" style="font-size:10rem" >WAVE</h1></div>
      </div>

      <h3 class="span loader" style="font-size:3rem" >
        <span class="m">T</span>
        <span class="m">E</span>
        <span class="m">C</span>
        <span class="m">H</span>
        <span class="m">N</span>
        <span class="m">O</span>
        <span class="m">L</span>
        <span class="m">O</span>
        <span class="m">G</span>
        <span class="m">Y</span>
      </h3>
    </div>
  </div>
</template>
<script setup>

import { loadFull } from 'tsparticles'

const particlesInit = async engine => {
  await loadFull(engine)
}

const particlesLoaded = async container => {
  console.log('Particles container loaded', container)
}
var c = document.getElementsByTagName("Canvas");

c.height = 1500
</script>
<style scoped>
#tsparticles{
      min-width: 100vw !important;
    min-height: 100vh !important;

     

}
canvas{
   min-height: 1366;

}
div .text{
margin: 90px 0 0 250px;
will-change: transform;
}

#ui {
  transform-style: preserve-3d;

}
#ui .text {
  position: absolute;
  font-size: 10rem;
  color: #fff;
  line-height: 15rem;
  font-family: 'Anton', sans-serif;

  mix-blend-mode: screen;
  transform-style: preserve-3d;
}
#ui .text:nth-child(1) {
  -webkit-clip-path: polygon(-30% 0, -20% 0, 20% 100%, 0% 100%);
  clip-path: polygon(-30% 0, -20% 0, 20% 100%, 0% 100%);
  -webkit-animation: wave 2000ms -10000ms ease-in-out infinite alternate;
  animation: wave 2000ms -10000ms ease-in-out infinite alternate;
}
#ui .text:nth-child(2) {
  -webkit-clip-path: polygon(-25% 0, -15% 0, 25% 100%, 5% 100%);
  clip-path: polygon(-25% 0, -15% 0, 25% 100%, 5% 100%);
  -webkit-animation: wave 2000ms -9800ms ease-in-out infinite alternate;
  animation: wave 2000ms -9800ms ease-in-out infinite alternate;
}
#ui .text:nth-child(3) {
  -webkit-clip-path: polygon(-20% 0, -10% 0, 30% 100%, 10% 100%);
  clip-path: polygon(-20% 0, -10% 0, 30% 100%, 10% 100%);
  -webkit-animation: wave 2000ms -9600ms ease-in-out infinite alternate;
  animation: wave 2000ms -9600ms ease-in-out infinite alternate;
}
#ui .text:nth-child(4) {
  -webkit-clip-path: polygon(-15% 0, -5% 0, 35% 100%, 15% 100%);
  clip-path: polygon(-15% 0, -5% 0, 35% 100%, 15% 100%);
  -webkit-animation: wave 2000ms -9400ms ease-in-out infinite alternate;
  animation: wave 2000ms -9400ms ease-in-out infinite alternate;
}
#ui .text:nth-child(5) {
  -webkit-clip-path: polygon(-10% 0, 0% 0, 40% 100%, 20% 100%);
  clip-path: polygon(-10% 0, 0% 0, 40% 100%, 20% 100%);
  -webkit-animation: wave 2000ms -9200ms ease-in-out infinite alternate;
  animation: wave 2000ms -9200ms ease-in-out infinite alternate;
}
#ui .text:nth-child(6) {
  -webkit-clip-path: polygon(-5% 0, 5% 0, 45% 100%, 25% 100%);
  clip-path: polygon(-5% 0, 5% 0, 45% 100%, 25% 100%);
  -webkit-animation: wave 2000ms -9000ms ease-in-out infinite alternate;
  animation: wave 2000ms -9000ms ease-in-out infinite alternate;
}
#ui .text:nth-child(7) {
  -webkit-clip-path: polygon(0% 0, 10% 0, 50% 100%, 30% 100%);
  clip-path: polygon(0% 0, 10% 0, 50% 100%, 30% 100%);
  -webkit-animation: wave 2000ms -8800ms ease-in-out infinite alternate;
  animation: wave 2000ms -8800ms ease-in-out infinite alternate;
}
#ui .text:nth-child(8) {
  -webkit-clip-path: polygon(5% 0, 15% 0, 55% 100%, 35% 100%);
  clip-path: polygon(5% 0, 15% 0, 55% 100%, 35% 100%);
  -webkit-animation: wave 2000ms -8600ms ease-in-out infinite alternate;
  animation: wave 2000ms -8600ms ease-in-out infinite alternate;
}
#ui .text:nth-child(9) {
  -webkit-clip-path: polygon(10% 0, 20% 0, 60% 100%, 40% 100%);
  clip-path: polygon(10% 0, 20% 0, 60% 100%, 40% 100%);
  -webkit-animation: wave 2000ms -8400ms ease-in-out infinite alternate;
  animation: wave 2000ms -8400ms ease-in-out infinite alternate;
}
#ui .text:nth-child(10) {
  -webkit-clip-path: polygon(15% 0, 25% 0, 65% 100%, 45% 100%);
  clip-path: polygon(15% 0, 25% 0, 65% 100%, 45% 100%);
  -webkit-animation: wave 2000ms -8200ms ease-in-out infinite alternate;
  animation: wave 2000ms -8200ms ease-in-out infinite alternate;
}
#ui .text:nth-child(11) {
  -webkit-clip-path: polygon(20% 0, 30% 0, 70% 100%, 50% 100%);
  clip-path: polygon(20% 0, 30% 0, 70% 100%, 50% 100%);
  -webkit-animation: wave 2000ms -8000ms ease-in-out infinite alternate;
  animation: wave 2000ms -8000ms ease-in-out infinite alternate;
}
#ui .text:nth-child(12) {
  -webkit-clip-path: polygon(25% 0, 35% 0, 75% 100%, 55% 100%);
  clip-path: polygon(25% 0, 35% 0, 75% 100%, 55% 100%);
  -webkit-animation: wave 2000ms -7800ms ease-in-out infinite alternate;
  animation: wave 2000ms -7800ms ease-in-out infinite alternate;
}
#ui .text:nth-child(13) {
  -webkit-clip-path: polygon(30% 0, 40% 0, 80% 100%, 60% 100%);
  clip-path: polygon(30% 0, 40% 0, 80% 100%, 60% 100%);
  -webkit-animation: wave 2000ms -7600ms ease-in-out infinite alternate;
  animation: wave 2000ms -7600ms ease-in-out infinite alternate;
}
#ui .text:nth-child(14) {
  -webkit-clip-path: polygon(35% 0, 45% 0, 85% 100%, 65% 100%);
  clip-path: polygon(35% 0, 45% 0, 85% 100%, 65% 100%);
  -webkit-animation: wave 2000ms -7400ms ease-in-out infinite alternate;
  animation: wave 2000ms -7400ms ease-in-out infinite alternate;
}
#ui .text:nth-child(15) {
  -webkit-clip-path: polygon(40% 0, 50% 0, 90% 100%, 70% 100%);
  clip-path: polygon(40% 0, 50% 0, 90% 100%, 70% 100%);
  -webkit-animation: wave 2000ms -7200ms ease-in-out infinite alternate;
  animation: wave 2000ms -7200ms ease-in-out infinite alternate;
}
#ui .text:nth-child(16) {
  -webkit-clip-path: polygon(45% 0, 55% 0, 95% 100%, 75% 100%);
  clip-path: polygon(45% 0, 55% 0, 95% 100%, 75% 100%);
  -webkit-animation: wave 2000ms -7000ms ease-in-out infinite alternate;
  animation: wave 2000ms -7000ms ease-in-out infinite alternate;
}
#ui .text:nth-child(17) {
  -webkit-clip-path: polygon(50% 0, 60% 0, 100% 100%, 80% 100%);
  clip-path: polygon(50% 0, 60% 0, 100% 100%, 80% 100%);
  -webkit-animation: wave 2000ms -6800ms ease-in-out infinite alternate;
  animation: wave 2000ms -6800ms ease-in-out infinite alternate;
}
#ui .text:nth-child(18) {
  -webkit-clip-path: polygon(55% 0, 65% 0, 105% 100%, 85% 100%);
  clip-path: polygon(55% 0, 65% 0, 105% 100%, 85% 100%);
  -webkit-animation: wave 2000ms -6600ms ease-in-out infinite alternate;
  animation: wave 2000ms -6600ms ease-in-out infinite alternate;
}
#ui .text:nth-child(19) {
  -webkit-clip-path: polygon(60% 0, 70% 0, 110% 100%, 90% 100%);
  clip-path: polygon(60% 0, 70% 0, 110% 100%, 90% 100%);
  -webkit-animation: wave 2000ms -6400ms ease-in-out infinite alternate;
  animation: wave 2000ms -6400ms ease-in-out infinite alternate;
}
#ui .text:nth-child(20) {
  -webkit-clip-path: polygon(65% 0, 75% 0, 115% 100%, 95% 100%);
  clip-path: polygon(65% 0, 75% 0, 115% 100%, 95% 100%);
  -webkit-animation: wave 2000ms -6200ms ease-in-out infinite alternate;
  animation: wave 2000ms -6200ms ease-in-out infinite alternate;
}
#ui .text:nth-child(21) {
  -webkit-clip-path: polygon(70% 0, 80% 0, 120% 100%, 100% 100%);
  clip-path: polygon(70% 0, 80% 0, 120% 100%, 100% 100%);
  -webkit-animation: wave 2000ms -6000ms ease-in-out infinite alternate;
  animation: wave 2000ms -6000ms ease-in-out infinite alternate;
}
#ui .text:nth-child(22) {
  -webkit-clip-path: polygon(75% 0, 85% 0, 125% 100%, 105% 100%);
  clip-path: polygon(75% 0, 85% 0, 125% 100%, 105% 100%);
  -webkit-animation: wave 2000ms -5800ms ease-in-out infinite alternate;
  animation: wave 2000ms -5800ms ease-in-out infinite alternate;
}
#ui .text:nth-child(23) {
  -webkit-clip-path: polygon(80% 0, 90% 0, 130% 100%, 110% 100%);
  clip-path: polygon(80% 0, 90% 0, 130% 100%, 110% 100%);
  -webkit-animation: wave 2000ms -5600ms ease-in-out infinite alternate;
  animation: wave 2000ms -5600ms ease-in-out infinite alternate;
}
#ui .text:nth-child(24) {
  -webkit-clip-path: polygon(85% 0, 95% 0, 135% 100%, 115% 100%);
  clip-path: polygon(85% 0, 95% 0, 135% 100%, 115% 100%);
  -webkit-animation: wave 2000ms -5400ms ease-in-out infinite alternate;
  animation: wave 2000ms -5400ms ease-in-out infinite alternate;
}
#ui .text:nth-child(25) {
  -webkit-clip-path: polygon(90% 0, 100% 0, 140% 100%, 120% 100%);
  clip-path: polygon(90% 0, 100% 0, 140% 100%, 120% 100%);
  -webkit-animation: wave 2000ms -5200ms ease-in-out infinite alternate;
  animation: wave 2000ms -5200ms ease-in-out infinite alternate;
}
#ui .text:nth-child(26) {
  -webkit-clip-path: polygon(95% 0, 105% 0, 145% 100%, 125% 100%);
  clip-path: polygon(95% 0, 105% 0, 145% 100%, 125% 100%);
  -webkit-animation: wave 2000ms -5000ms ease-in-out infinite alternate;
  animation: wave 2000ms -5000ms ease-in-out infinite alternate;
}

@-webkit-keyframes wave {
  0% {
    transform: translate(-50%, -50%) scale(0.95) rotateX(5deg) rotateY(5deg)
      rotateZ(0deg);
    color: #001e64;
  }
  100% {
    transform: translate(-50%, -50%) scale(1.05) rotateX(0deg) rotateY(0deg)
      rotateZ(0deg);
    color: #32e6ff;
  }
}

@keyframes wave {
  0% {
    transform: translate(-50%, -50%) scale(0.95) rotateX(5deg) rotateY(5deg)
      rotateZ(0deg);
    color: #001e64;
  }
  100% {
    transform: translate(-50%, -50%) scale(1.05) rotateX(0deg) rotateY(0deg)
      rotateZ(0deg);
    color: #32e6ff;
  }
}
.mainTitle {
  text-shadow: 0 0 2px;
}
.title {
  transition: 0.3s;
  color:#66df49
}
.nav,
.slider {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  position: relative;
  background-color: #1e1f26;
  text-align: center;
  padding: 0 2em;
}

.nav h1,
.slider h1 {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 5vw;
  margin: 0;
  padding-bottom: 0.5rem;
  letter-spacing: 0.5rem;
  color: #03dac6;
  transition: all 0.3s ease;
  z-index: 3;
}
h1{


}
.title:hover {
    color: #fff;
text-shadow:   0 0 5px #66df49, 0 0 10px #66df49, 0 0 15px #66df49,
      0 0 20px #66df49, 0 0 25px #66df49, 0 0 30px #66df49, 0 0 35px #66df49,
      0 0 40px #66df49, 0 0 50px #66df49;
}

.slider h2 {
  font-size: 2vw;
  letter-spacing: 0.3rem;
  font-family: 'ROBOTO', sans-serif;
  font-weight: 300;
  color: #faebd7;
  z-index: 4;
}
h3.span {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  font-size: 2.6vw;
  letter-spacing: 0.7em;
  font-family: 'ROBOTO', sans-serif;
  font-weight: 300;

  color: #faebd7;
  z-index: 4;
  transition: 0.3s;
}
span:hover {
  color: black;
  transform: translateX(25px);
}

a {
  text-decoration: none;
}

.nav-container {
  display: flex;
  flex-direction: row;
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 75px;
  box-shadow: 20px 20px 50px rgba(0, 0, 0, 0.5);
  background: #1e1f26;
  z-index: 10;
  transition: all 0.3s cubic-bezier(0.19, 1, 0.22, 1);
}

.nav-container--top-first {
  position: fixed;
  top: 75px;
  transition: all 0.3s cubic-bezier(0.19, 1, 0.22, 1);
}

.nav-container--top-second {
  position: fixed;
  top: 0;
}
.nav-tab {
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 1;
  color: #03dac6;
  letter-spacing: 0.1rem;
  transition: all 0.5s ease;
  font-size: 2vw;
}

.nav-tab:hover {
  color: #1e1f26;
  background: #03dac6;
  transition: all 0.5s ease;
}

.nav-tab-slider {
  position: absolute;
  bottom: 0;
  width: 0;
  height: 2px;
  background: #03dac6;
  transition: left 0.3s ease;
}
.background {
  position: absolute;
  height: 90vh;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: auto;
}
@media (min-width: 800px) {
  .nav h1,
  .slider h1 {
    font-size: 5vw;
  }

  .nav h2,
  .slider h2 {
    font-size: 3vw;
  }

  .nav-tab {
    font-size: 3vw;
  }
}

@media screen and (min-width: 360px) {
  .nav h1,
  .slider h1 {
    font-size: 8vw;
  }

  .nav h2,
  .slider h2 {
    font-size: 2vw;
    letter-spacing: 0.2vw;
  }

  .nav-tab {
    font-size: 1.2vw;
  }
}
.background {
  position: absolute;
  height: 100vh;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 0;
}
.loader span:nth-child(n + 6) {
  color: #faebd7;
  text-shadow: 0 0 0 #faebd7;
  animation: loading 1s ease-in-out infinite alternate;

  -webkit-animation: loading 1s ease-in-out infinite alternate;
}
.loader span:nth-child(-n + 5) {
  color: #faebd7;
  text-shadow: 0 0 0 #faebd7;
  animation: loadingGreen 1s ease-in-out infinite alternate;

  -webkit-animation: loadingGreen 1s ease-in-out infinite alternate;
}

@keyframes loading {
  from {
    color: #fff;
    text-shadow: 0 0 5px #009bdb, 0 0 10px #009bdb, 0 0 15px #009bdb,
      0 0 20px #009bdb, 0 0 25px #009bdb, 0 0 30px #009bdb, 0 0 35px #009bdb,
      0 0 40px #009bdb, 0 0 50px #009bdb;
  }

  to {
    color: #009bdb;

    text-shadow: 0 0 5px #009bdb, 0 0 10px #009bdb, 0 0 15px #009bdb;
  }
}
@keyframes loadingGreen {
  from {
    color: #fff;
    text-shadow: 0 0 5px #66df49, 0 0 10px #66df49, 0 0 15px #66df49,
      0 0 20px #66df49, 0 0 25px #66df49, 0 0 30px #66df49, 0 0 35px #66df49,
      0 0 40px #66df49, 0 0 50px #66df49;
  }

  to {
    color: #66df49;
    text-shadow: 0 0 5px #66df49, 0 0 6px #66df49, 0 0 7px #66df49;
  }
}
.loader span {
  animation-delay: 0.1s;

  -webkit-animation-delay: 0.1s;
}

span:nth-child(-n + 5) {
  color: #66df49;
}
</style>
