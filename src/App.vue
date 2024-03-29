<script setup>
import mediaList from "./components/mediaList.vue";
import markList from "./components/markList.vue";
const reloadWithoutCache = () => {
  let currentUrl = window.location.href;
  currentUrl = currentUrl.split("#")[0];
  const uniqueTimeStamp = new Date().getTime();
  if (currentUrl.includes("?")) {
    currentUrl += "&_=" + uniqueTimeStamp;
  } else {
    currentUrl += "?_=" + uniqueTimeStamp;
  }
  window.location.href = currentUrl;
};
</script>

<template>
  <main>
    <div class="app-wrap">
      <button class="reloadBtn" @click="reloadWithoutCache">重新載入</button>
      <mediaList />
      <markList />
    </div>
  </main>
</template>

<style lang="scss">
.title {
  padding-top: 50px;
  text-align: center;
  font-size: 34px;
}
.reloadBtn {
  position: fixed;
  top: 20px;
  right: 20px;
}
</style>
