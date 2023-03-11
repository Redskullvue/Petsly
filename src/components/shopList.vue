<template>
  <div
    :class="{
      'h-screen': showShop,
      'translate-y-full': !showShop,
    }"
    class="transition-all ease-in-out duration-200 z-50"
  >
    <div
      v-if="showShop"
      class="w-screen h-screen test mb-4 flex flex-col justify-start gap-y-4 overflow-scroll z-40 absolute top-0 bg-white rounded-bl-3xl rounded-br-3xl"
    >
      <div
        class="flex flex-col px-4 py-2 gap-y-10 items-center justify-center w-full bg-blue-800 rounded-br-xl rounded-bl-xl"
      >
        <img
          class="w-28 h-28 rounded-full"
          src="../assets/images/DogShop.png"
          alt="image"
        />
        <h2 class="text-white mb-2 font-bold">پت شاپ داگ</h2>
        <button
          @click="closeShopList"
          class="top-1 absolute right-1 text-white font-bold cursor-pointer"
        >
          X
        </button>
      </div>
      <ul>
        <li v-for="i in 5" class="my-8 mx-4" :key="i"><y-product-card /></li>
      </ul>
    </div>
  </div>
</template>

<script>
import YProductCard from "./productcard.vue";
export default {
  name: "shopList",
  components: {
    YProductCard,
  },
  props: ["showShop"],
  methods: {
    closeShopList() {
      this.$emit("closeShop", false);
    },
  },
};
</script>

<style>
.test {
  height: 85% !important;
}
</style>
