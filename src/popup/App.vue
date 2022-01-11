<!--
 * @Descripttion: 
 * @version: 0.x
 * @Author: zhai
 * @Date: 2022-01-11 14:55:01
 * @LastEditors: zhai
 * @LastEditTime: 2022-01-11 15:46:28
-->
<template>
  <div className="app">
    <!-- <img :src="logo" className="logo" /> -->
    <Code msg="Welcome to Your Vue.js App" />
 
    <!-- <div class="btn-wrapper">
      <div
        @click="goToOptions"
        class="crx-btn"
        :style="{ width: '150px', height: '30px', lineHeight: '30px', cursor: 'pointer' }"
      >
        Go to Options Page
      </div>
    </div> -->
  </div>
</template>

<script>
import Code from "./components/Code.vue";

// get static files by chrome.runtime.getURL
const logo = chrome.runtime.getURL('assets/create-crx-app.png')
export default {
  name: 'App',
  components: {
    Code
  },
  data: function() {
    return {
      logo,
    };
  },

  methods: {
    goToOptions() {
      // go to options page
      chrome.runtime.openOptionsPage()
    }
  }
}
</script>

<style lang="less" scoped>
@import "../style/popup.less";
</style>
