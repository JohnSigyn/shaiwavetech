<template>
  <!-- <div id="canvasId"></div> -->
  <div class="overflow-x-hidden stacking-slide">
    <Main />
    <Ocean></Ocean>
    <AnimationOnScroll />
    <Clients/>
    <Contacts/>
    <!-- <div>
      <PlanetOrbit/>
    </div> -->

     
  </div>
</template>
<script setup></script>

<script>
import Main from '../src/components/Main.vue'
import AnimationOnScroll from '../src/components/AnimationOnScroll.vue'
import PlanetOrbit from '../src/components/PlanetOrbit.vue'
import Ocean from '../src/components/OceanECommerce.vue'
import Clients from '../src/components/Clients.vue'
import Contacts from '../src/components/Contacts.vue'
import { ref } from '@vue/reactivity'
import { animate } from 'tsparticles-engine'

export default {
  components: {
    Main,
    AnimationOnScroll,
    PlanetOrbit,
    Ocean,
    Clients,
    Contacts
  }
}
</script>
<style scoped>
#app {
  font-family: 'Ruluko', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.stacking-slide {
  width: 100%;
  position: sticky;
  top: 0;
}
</style>
