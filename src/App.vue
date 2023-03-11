<template>
  <div dir="rtl" class="h-screen font-vazir">
    <div class="fixed top-0 w-screen z-20">
      <y-header />
      <y-shop-list :showShop="showShop" @closeShop="shopListToggle" />
    </div>
    <div class="w-screen h-screen">
      <y-map @shopToggle="shopListToggle" class="p-2" />
    </div>
  </div>
</template>

<script>
import YHeader from "./components/Header.vue";
import YMap from "./components/map.vue";
import YShopList from "./components/shopList.vue";
import "./output.css";
export default {
  name: "App",
  components: {
    YHeader,
    YMap,
    YShopList,
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
