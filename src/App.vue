<template>
  <!-- <div id="canvasId"></div> -->
  <div class="overflow-x-hidden stacking-slide">
    <Main />
    <Ocean></Ocean>
    <AnimationOnScroll />

    <div>
      <PlanetOrbit/>
    </div>
  </div>
</template>
<script setup></script>

<script>
import Main from '../src/components/Main.vue'
import AnimationOnScroll from '../src/components/AnimationOnScroll.vue'
import PlanetOrbit from '../src/components/PlanetOrbit.vue'
import Ocean from '../src/components/OceanECommerce.vue'
import { ref } from '@vue/reactivity'
import { animate } from 'tsparticles-engine'

export default {
  components: {
    Main,
    AnimationOnScroll,
    PlanetOrbit,
    Ocean
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
