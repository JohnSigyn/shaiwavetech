<template>
  <div class="overflow-x-hidden stacking-slide">
    <Main />
    <div class="">
      <div class="">
        <AnimationOnScroll />
      </div>
    </div>
  </div>
</template>
<script>
import Main from '../src/components/Main.vue'
import AnimationOnScroll from '../src/components/AnimationOnScroll.vue'
export default {
  components: {
    Main,
    AnimationOnScroll
  }
}
</script>
<style scoped>
.stacking-slide{
     width: 100%;
    position: sticky;
    top: 0;
}
</style>
