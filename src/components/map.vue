<template>
  <mgl-map
    mapStyle="https://api.maptiler.com/maps/streets/style.json?key=Hy2cvl9hYfTfrPh40tyk"
    :zoom="14"
    :center="[51.361654, 35.755671]"
    @click="shopToggle"
  >
    <div>
      <mgl-marker
        :coordinates="[51.361654, 35.755671]"
        color="#FFB6C1"
        :scale="1.5"
      >
      </mgl-marker>
    </div>
    <button class="absolute bottom-16 right-4 bg-white rounded-2xl p-4">
      <i-gps />
    </button>
    <div
      v-if="!hasError"
      class="z-10 absolute bottom-6 left-4 rounded-xl p-2 bg-white"
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
    // This is a Request for the current address Unfortunetly the api dosent support FA
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
    //This is to check if the shop list should be open or not
    shopToggle() {
      this.shopOpen = !this.shopOpen;
      this.$emit("shopToggle", this.shopOpen);
    },
  },
};
</script>

<style lang="scss">
// MapLibre Styles are lkoaded by SASS so we added this sass file here
@import "~vue-maplibre-gl/src/css/maplibre.scss";
</style>
