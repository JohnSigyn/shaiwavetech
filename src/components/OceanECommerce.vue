<template>
  <div class="mainContainer " style="background:#0f172a">
    <TransitionRoot appear :show="isOpen" as="template">
      <Dialog as="div" @close="closeModal" class="relative z-10">
        <TransitionChild
          as="template"
          enter="duration-300 ease-out"
          enter-from="opacity-0"
          enter-to="opacity-100"
          leave="duration-200 ease-in"
          leave-from="opacity-100"
          leave-to="opacity-0"
        >
          <div class="fixed inset-0 bg-black bg-opacity-75" />
        </TransitionChild>

        <div class="fixed inset-0 overflow-y-auto">
          <div
            class="flex min-h-full items-center justify-center p-4 text-center"
          >
            <TransitionChild
              as="template"
              enter="duration-300 ease-out"
              enter-from="opacity-0 scale-95"
              enter-to="opacity-100 scale-100"
              leave="duration-200 ease-in"
              leave-from="opacity-100 scale-100"
              leave-to="opacity-0 scale-95"
            >
              <DialogPanel
                class="w-full max-w-md transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all"
                style="min-width:80vw"
              >
                <DialogTitle
                  as="h3"
                  class="text-lg font-medium leading-6 text-gray-900"
                >
                </DialogTitle>
                <!-- <div class="mt-2">
                  <p class="text-sm text-gray-500">
                   
                  </p>
                </div> -->

                <div class="flex flex-row-reverse absolute right-8 z-50 top-8">
                  <button
                    type="button"
                    class="inline-flex justify-center rounded-md border border-transparent bg-blue-100 px-4 py-2 text-sm font-medium text-blue-900 hover:bg-blue-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-500 focus-visible:ring-offset-2"
                    @click="closeModal"
                  >
                    Close
                  </button>
                </div>

                <div class="rounded-lg relative">
                 <div
                    v-if="imgIndex == 1"
                    src="../assets/planspricing.webp"
                    class="rounded-lg"
                    width="100px"
                    alt=""
                  >First page insert here</div>
                
              
                  <div
                    v-if="imgIndex == 2"
                    src="../assets/planspricing.webp"
                    class="rounded-lg"
                    width="100px"
                    alt=""
                  >
                  Second page to insert here
                  </div>
               
                </div>
              </DialogPanel>
            </TransitionChild>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
    <main class="page-content">
      <div class="card">
        <div class="content">
          <h2 class="title">Ocean E-Commerce</h2>
          <p class="copy">
            Welcome to Ocean E-Commerce
          </p>
          <button class="btn" @click="openModal(1)">View More</button>
        </div>
      </div>
      <div class="card">
        <div class="content">
          <h2 class="title">Ocean POS System</h2>
          <p class="copy">
            Choose among these options based on your budget
          </p>
          <button class="btn" @click="openModal(2)">
            View Pricing Details
          </button>
        </div>
      </div>
      <div class="card">
        <div class="content">
          <h2 class="title">Plant Disease Detection</h2>
          <p class="copy">Enter your store details to apply</p>
          <button class="btn">Future Plan</button>
        </div>
      </div>
      <div class="card">
        <div class="content">
          <h2 class="title">Smart City Project</h2>
          <p class="copy">
            We thank you for chosing our company. In case of any grievances or
            issues please contact us.
          </p>
          <button class="btn">Future Plan</button>
        </div>
      </div>
    </main>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import {
  TransitionRoot,
  TransitionChild,
  Dialog,
  DialogPanel,
  DialogTitle
} from '@headlessui/vue'
const isOpen = ref(false)
let imgIndex = ref(0)

function closeModal () {
  isOpen.value = false
}

</script>
<script>
export default {
  data () {
    return {
      imgIndex: 10
    }
  },
  methods: {
    openModal (index) {
  console.log(index)
      this.isOpen = true
      this.imgIndex = index
    }
  }
}
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css?family=Cardo:400i|Rubik:400,700&display=swap');

* {
  box-sizing: border-box;
}

html,
body {
  height: 100%;
}

body {
  display: grid;
  place-items: center;
}

.mainContainer {
  min-height: 106vh;
  display: flex;
  place-items: center;
}
.page-content {
  display: grid;
  grid-gap: 3rem;
  padding: 1rem;
  max-width: 90vw;
  margin: 0 auto;
  font-family: var(--font-sans);
}
@media (min-width: 600px) {
  .page-content {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (min-width: 800px) {
  .page-content {
    grid-template-columns: repeat(4, 1fr);
  }
}

.card {
  position: relative;
  display: flex;
  align-items: flex-end;
  overflow: hidden;
  padding: 1rem;
  width: 100%;
  text-align: center;
  color: whitesmoke;
  background-color: whitesmoke;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1), 0 2px 2px rgba(0, 0, 0, 0.1),
    0 4px 4px rgba(0, 0, 0, 0.1), 0 8px 8px rgba(0, 0, 0, 0.1),
    0 16px 16px rgba(0, 0, 0, 0.1);
}
@media (min-width: 600px) {
  .card {
    height: 43vh;
    border-radius: 10px;
  }
}
.card:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 110%;
  background-size: cover;
  background-position: 0 0;
  transition: transform calc(700ms * 1.5) cubic-bezier(0.19, 1, 0.22, 1);
  pointer-events: none;
}
.card:after {
  content: '';
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 200%;
  pointer-events: none;
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0) 0%,
    rgba(0, 0, 0, 0.009) 11.7%,
    rgba(0, 0, 0, 0.034) 22.1%,
    rgba(0, 0, 0, 0.072) 31.2%,
    rgba(0, 0, 0, 0.123) 39.4%,
    rgba(0, 0, 0, 0.182) 46.6%,
    rgba(0, 0, 0, 0.249) 53.1%,
    rgba(0, 0, 0, 0.32) 58.9%,
    rgba(0, 0, 0, 0.394) 64.3%,
    rgba(0, 0, 0, 0.468) 69.3%,
    rgba(0, 0, 0, 0.54) 74.1%,
    rgba(0, 0, 0, 0.607) 78.8%,
    rgba(0, 0, 0, 0.668) 83.6%,
    rgba(0, 0, 0, 0.721) 88.7%,
    rgba(0, 0, 0, 0.762) 94.1%,
    rgba(0, 0, 0, 0.79) 100%
  );
  transform: translateY(-50%);
  transition: transform calc(700ms * 2) cubic-bezier(0.19, 1, 0.22, 1);
}
.card:nth-child(1):before {
  background-image: url('../assets/commerce.jpg');

}
.card:nth-child(2):before {
  background-image: url('../assets/cardAssets/POS.svg');
}
.card:nth-child(3):before {
  background-image: url('../assets/cardAssets/PlantDiseaseDetection.svg');
}
.card:nth-child(4):before {
  background-image: url('../assets/cardAssets/SmartCity.svg');
}

.content {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  padding: 1rem;
  transition: transform 700ms cubic-bezier(0.19, 1, 0.22, 1);
  z-index: 1;
}
.content > * + * {
  margin-top: 1rem;
}

.title {
  font-size: 1.3rem;
  font-weight: bold;
  line-height: 1.2;
}

.copy {
  display: none;
  font-family: var(--font-serif);
  font-size: 1.125rem;
  font-style: italic;
  line-height: 1.35;
}

.btn {
  cursor: pointer;
  margin-top: 1.5rem;
  padding: 0.75rem 1.5rem;
  font-size: 0.65rem;
  font-weight: bold;
  letter-spacing: 0.025rem;
  text-transform: uppercase;
  color: white;
  background-color: black;
  border: none;
}
.btn:hover {
  background-color: #0d0d0d;
}
.btn:focus {
  outline: 1px dashed yellow;
  outline-offset: 3px;
}

@media (hover: hover) and (min-width: 600px) {
  .card:after {
    transform: translateY(0);
  }

  .content {
    transform: translateY(calc(100% - 4.5rem));
  }
  .content > *:not(.title) {
    opacity: 0;
    transform: translateY(1rem);
    transition: transform 700ms cubic-bezier(0.19, 1, 0.22, 1),
      opacity 700ms cubic-bezier(0.19, 1, 0.22, 1);
  }

  .card:hover,
  .card:focus-within {
    align-items: center;
  }
  .card:hover:before,
  .card:focus-within:before {
    transform: translateY(-4%);
  }
  .card:hover:after,
  .card:focus-within:after {
    transform: translateY(-50%);
  }
  .card:hover .content,
  .card:focus-within .content {
    transform: translateY(0);
  }
  .card:hover .content > *:not(.title),
  .card:focus-within .content > *:not(.title) {
    opacity: 1;
    transform: translateY(0);
    transition-delay: calc(700ms / 8);
  }

  .card:focus-within:before,
  .card:focus-within:after,
  .card:focus-within .content,
  .card:focus-within .content > *:not(.title) {
    transition-duration: 0s;
  }
}
</style>
