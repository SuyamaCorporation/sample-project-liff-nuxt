<template>
  <button class="center-button" @click.prevent="fetchApi">API通信</button>
  <div id="message">{{ message }}</div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { liff } from '@line/liff'

const message = ref('')

async function fetchApi() {
  message.value = '通信中...'

  const idToken = liff.getIDToken();

  $fetch('あなたのサーバーのURL', {
    method: 'GET',
    headers: {
      'Content-Type': 'application/json',
    },
    params: {
      "idToken": idToken
    },
  })
    .then((response) => message.value = response.message)
    .catch((error) => message.value = error.message)
}

onMounted(() => {
  liff.init({ liffId: 'あなたのLIFFID' })
    .then(() => {
      console.log('LIFF init success')
    })
    .catch((err) => {
      console.error(err)
      if (!process.env.liffId) {
        console.info('`LIFF_ID` が設定されていません。');
      }
    })
})

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
  flex-direction: column;
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
  margin-bottom: 20px;
}

.center-button:hover {
  background-color: #45a049;
}

/* メッセージのスタイル */
#message {
  font-size: 16px;
  color: #333;
  margin-top: 10px;
}
</style>