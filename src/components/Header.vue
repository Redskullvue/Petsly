<template>
  <div
    class="bg-white flex items-center gap-x-4 px-4 py-6 rounded-br-3xl rounded-bl-3xl shadow-2xl shadow-slate-700"
  >
    <div @click="isOpen = !isOpen" class="mt-4">
      <i-menu />
    </div>
    <div class="mt-4">
      <input
        v-model="searchValue"
        class="outline-none"
        type="text"
        placeholder="جستجو..."
        @focus="searchValue = ''"
      />
    </div>
  </div>
  <div>
    <!-- The Close button is inside the side bar so its emitting and come back here to get processed -->
    <y-sideBar :status="isOpen" @closeSideBar="checkStatus" />
  </div>
</template>

<script>
import { iMenu } from "./icons/index";
import YSideBar from "./sidebar.vue";
export default {
  name: "HelloWorld",
  components: {
    iMenu,
    YSideBar,
  },
  data() {
    return {
      // Side Bar
      isOpen: false,
      searchValue: "",
    };
  },
  methods: {
    // To check and see if the side bar is open or not
    checkStatus() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>
