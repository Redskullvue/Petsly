<template>
  <div
    class="flex items-center justify-between w-full bg-gray-200 p-1 rounded-lg"
  >
    <div class="flex gap-x-2">
      <div>
        <img
          class="rounded-xl w-16 h-16"
          src="../assets/images/Food.png"
          alt="food image"
        />
      </div>
      <div class="text-center my-1 mx-1">
        <h2 class="font-bold text-lg">غذای هلثی فود</h2>
        <h4 class="text-gray-500 text-xs">برند هیمالاوا</h4>
      </div>
    </div>
    <button
      class="text-center p-1 px-3 bg-blue-800 text-xs text-white rounded-md mx-1 hover:bg-blue-900"
    >
      افزودن به سبد
    </button>
  </div>
</template>

<script>
export default {
  name: "productCard",
};
</script>
