<template>
  <div
    v-if="status"
    class="bg-white shadow-lg w-2/3 h-screen fixed top-0 !z-50 md:w-1/3 transition-all"
  >
    <div
      class="bg-black rounded-br-2xl shadow-gray-400 shadow-lg rounded-bl-2xl flex items-center justify-center p-10 relative"
    >
      <button
        @click="checkStatus"
        class="absolute font-bold right-2 top-2 rounded-lg transition ease-in-out bg-white hover:-translate-y-1 hover:scale-110 duration-300"
      >
        <i-back />
      </button>
      <img
        class="rounded-full w-28 h-28 m-2"
        src="../assets/images/Petshop.png"
        alt="Pic"
      />
    </div>
    <div class="mt-6 p-4">
      <ul class="flex gap-y-2 flex-col">
        <li
          class="flex items-center gap-x-4 h-10 hover:cursor-pointer hover:font-bold"
        >
          <span><i-account /></span>پروفایل
        </li>
        <li
          class="flex items-center gap-x-4 h-10 hover:cursor-pointer hover:font-bold"
        >
          <i-bell />
          پرداخت ها
        </li>
        <li
          class="flex items-center gap-x-4 h-10 hover:cursor-pointer hover:font-bold"
        >
          <i-info />
          درباره ما
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { iAccount, iBell, iInfo, iBack } from "./icons/index";
export default {
  name: "YSideBar",
  props: ["status"],
  components: {
    iAccount,
    iBell,
    iInfo,
    iBack,
  },
  methods: {
    checkStatus() {
      this.$emit("closeSideBar", false);
    },
  },
};
</script>

<style></style>
