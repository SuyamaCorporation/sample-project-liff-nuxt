<template>
  <button class="center-button">API通信</button>
</template>

<script setup>
import { ref } from 'vue'

definePageMeta({
  title: 'API通信',
  description: 'API通信のサンプルページです。',
})
</script>

<style>
body,
html {
  height: 100%;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial, sans-serif;
}

/* ボタンのスタイル */
.center-button {
  padding: 10px 20px;
  font-size: 18px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.center-button:hover {
  background-color: #45a049;
}
</style>