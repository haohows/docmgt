<template>
  <div v-if="data.length > 0">
    <div class="title">圖像檔列表</div>
    <hr />
    <div class="list-wrap">
      <div v-for="(item, index) in data" :key="index">
        <div class="imgcard">
          <div
            class="imgItem"
            :style="`background-image: url('${baseUrl}${item.file}')`"
          ></div>
          <button class="btn" @click="copyUrl(item.file)">取得連結</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import Swal from "sweetalert2";

import { computed } from "vue";
const data = getImgDoc();
const copyUrl = (url) => {
  let textarea = document.createElement("textarea");
  let origin = location.origin;
  let pathname = location.pathname;
  textarea.value = `${origin}${pathname}image/${url}`;
  document.body.appendChild(textarea);
  textarea.select();
  textarea.setSelectionRange(0, 99999); // 確保兼容性
  // 執行複製操作
  document.execCommand("copy");

  // 從DOM中移除textarea元素
  document.body.removeChild(textarea);

  // 可選：給用戶一些反饋
  Swal.fire({
    icon: "success", //error\warning\info\question
    title: "網址已複製",
    text: textarea.value,
    timer: 1000,
    showConfirmButton: false,
  });
};
const baseUrl = computed(() => {
  let origin = location.origin;
  let pathname = location.pathname;
  let base = `${origin}${pathname}image/`;
  return base;
});
</script>

<style lang="scss">
.list-wrap {
  margin: 20px auto 250px;
  width: 80vw;
  // max-width: 1000px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
.imgItem {
  width: 140px;
  height: 140px;
  background-image: url();
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
}
.imgcard {
  margin: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  border: 1px solid black;
  padding: 10px;
  border-radius: 8px;
  background: #eee;
}
.btn {
  margin-top: 6px;
  width: 100%;
  padding: 5px;
  background-color: #fff;
  cursor: pointer;
}
</style>
