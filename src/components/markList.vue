<template>
  <div v-if="data.length > 0">
    <div class="title">標記檔資料庫</div>
    <hr />
    <div class="list-wrap">
      <div v-for="(item, index) in data" :key="index">
        <div class="markcard">
          <div class="markItem">AR</div>
          <div class="markText">{{ item.text }}</div>
          <button class="btn" @click="copyUrl(item.file)">取得連結</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";
const data = getMarkDoc();
const copyUrl = (url) => {
  let domain = location.origin;
  let textarea = document.createElement("textarea");
  textarea.value = `${domain}/mark/${url}`;
  document.body.appendChild(textarea);
  textarea.select();
  textarea.setSelectionRange(0, 99999); // 確保兼容性
  // 執行複製操作
  document.execCommand("copy");

  // 從DOM中移除textarea元素
  document.body.removeChild(textarea);

  // 可選：給用戶一些反饋
  alert("網址已複製");
};
</script>

<style lang="scss">
.list-wrap {
  margin: 0px auto 50px;
  width: 80vw;
  // max-width: 1000px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
.markItem {
  width: 140px;
  height: 60px;
  font-size: 50px;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
}
.markText {
  width: 140px;
  color: white;
  font-size: 14px;
  margin: 5px;
  text-align: center;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2; /* 限制在两行文本 */
  overflow: hidden;
  line-height: 1.2em;
  height: 2.4em; /* line-height * n行，这里是2行 */
}
.markcard {
  margin: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  border: 1px solid black;
  padding: 10px;
  border-radius: 8px;
  background: #3a3a3a;
}
.btn {
  margin-top: 6px;
  width: 100%;
  padding: 5px;
  background-color: #fff;
  cursor: pointer;
}
</style>
