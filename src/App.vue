<template>
  <div dir="rtl" class="h-screen">
    <div class="fixed top-0 w-screen z-20">
      <y-header />
    </div>
    <div class="w-screen h-screen">
      <div
        v-if="showShop"
        class="w-screen h-auto flex flex-col justify-start gap-y-4 overflow-scroll absolute top-0 z-40 ease-in-out duration-500 bg-white"
      >
        <div
          class="flex flex-col px-4 py-2 gap-y-8 items-center justify-center w-full bg-blue-800 rounded-br-xl rounded-bl-xl"
        >
          <img
            class="w-28 h-28 rounded-full"
            src="./assets/images/DogShop.png"
            alt="image"
          />
          <h2 class="text-white mb-2">پت شاپ داگ</h2>
          <button
            @click="showShop = !showShop"
            class="top-1 absolute right-1 text-white font-bold cursor-pointer"
          >
            X
          </button>
        </div>
        <ul>
          <li v-for="i in 6" class="m-4" :key="i"><y-product-card /></li>
        </ul>
      </div>
      <y-map @shopToggle="shopListToggle" />
    </div>
  </div>
</template>

<script>
import YHeader from "./components/Header.vue";
import YMap from "./components/map.vue";
import YProductCard from "./components/productcard.vue";

import "./output.css";
export default {
  name: "App",
  components: {
    YHeader,
    YMap,
    YProductCard,
  },
  data() {
    return {
      showShop: false,
    };
  },
  methods: {
    //This Method will toggle the shop list
    shopListToggle() {
      this.showShop = !this.showShop;
    },
  },
};
</script>
