<template>
  <mgl-map
    mapStyle="https://api.maptiler.com/maps/streets/style.json?key=Hy2cvl9hYfTfrPh40tyk"
    :zoom="14"
    :center="[51.361654, 35.755671]"
    @click="shopToggle"
  >
    <button
      class="z-50 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-10 h-10"
    >
      <mgl-marker
        :coordinates="[51.361654, 35.755671]"
        color="#FFB6C1"
        :scale="1.5"
        :clickTolerance="50"
      >
      </mgl-marker>
    </button>
    <div class="bg-blue-500 font-bold text-2xl z-50">Test</div>
    <button class="absolute bottom-16 right-4 bg-white rounded-2xl p-4">
      <i-gps />
    </button>
    <div
      v-if="!hasError"
      class="z-20 absolute bottom-6 left-4 rounded-xl p-2 bg-white"
    >
      <i-location />
    </div>
    <span
      class="absolute bottom-7 left-2 mx-4 w-1/2 overflow-hidden h-5 text-xs px-1 bg-gray-400 opacity-50"
      ><p>آدرس حال : {{ currentAddress }}</p></span
    >
  </mgl-map>
</template>

<script>
// //////////////////////////////////////////
// This Is Vue Maplibre Library which use Sass for the style of the map
// Its a simple library for vue js to use maps
// Docs can be find on https://github.com/razorness/vue-maplibre-gl
// /////////////////////////////////////////
import { MglMap, MglMarker } from "vue-maplibre-gl";
import { IGps, ILocation } from "./icons/index";
import axios from "axios";
export default {
  name: "YMap",
  components: {
    MglMap,
    MglMarker,
    IGps,
    ILocation,
  },
  data() {
    return {
      shopOpen: false,
      currentAddress: "",
      hasError: false,
    };
  },
  created() {
    axios
      .get(
        "https://api.maptiler.com/geocoding/51.361654,35.755671.json?key=Hy2cvl9hYfTfrPh40tyk"
      )
      .then((res) => {
        this.currentAddress = res.data.features[0].place_name;
      })
      .catch((err) => {
        console.log(err);
        this.hasError = true;
      });
  },
  methods: {
    shopToggle() {
      this.shopOpen = !this.shopOpen;
      this.$emit("shopToggle", this.shopOpen);
      console.log(document.getElementById("marker"));
    },
  },
};
</script>

<style lang="scss">
@import "~vue-maplibre-gl/src/css/maplibre.scss";
.marker {
  background-image: url("../assets/images/Petshop.png");
}
</style>
