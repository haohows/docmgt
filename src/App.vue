<script setup>
import mediaList from "./components/mediaList.vue";
</script>

<template>
  <main>
    <div class="app-wrap">
      <div class="title"> 圖檔資料庫</div>
      <hr />
      <mediaList />
    </div>
  </main>
</template>

<style lang="scss">
.title{
  padding-top: 50px;
  text-align: center;
  font-size: 34px;
}
</style>
