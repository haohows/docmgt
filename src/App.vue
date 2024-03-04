<script setup>
import mediaList from "./components/mediaList.vue";
import markList from "./components/markList.vue";
</script>

<template>
  <main>
    <div class="app-wrap">

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
</style>
