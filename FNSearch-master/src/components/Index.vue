<template>
  <el-container style="height: 100%">
    <el-header style="height: 40px" v-if="this.switchvalue === false">
      <LocalHeaders />
    </el-header>
    <el-main class="search-center" v-if="this.switchvalue === false">
      <search-windows ref="searchwindows" style="padding-bottom: 10%" />
    </el-main>
    <el-main v-if="this.switchvalue === true">
      <advanced-search style="padding-bottom: 10%" />
    </el-main>
    <el-footer style="height: 40px">
      <el-switch
        v-model="switchvalue"
        inactive-text="普通检索"
        active-text="高级检索"
      >
      </el-switch>
      <copy-right />
    </el-footer>
  </el-container>
</template>
<script>
import SearchWindows from "./SearchWindows.vue";
import CopyRight from "./CopyRight.vue";
import LocalHeaders from "./LocalHeaders.vue";
import AdvancedSearch from "./AdvancedSearch.vue";

export default {
  name: "index",
  components: {
    SearchWindows,
    CopyRight,
    LocalHeaders,
    AdvancedSearch,
  },
  data() {
    return {
      switchvalue: false,
    };
  },
  created() {
    let body = document.querySelector("body");
    body.addEventListener(
      "click",
      (e) => {
        this.$refs.searchwindows.deletsuggestlist();
      },
      false
    );
  },
};
</script>
<style scoped>
.search-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
