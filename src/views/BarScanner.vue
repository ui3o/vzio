<script setup lang="ts">
// @ts-ignore
import * as  QRCodeScanner from '../components/QRCodeScanner.vue'
import { ref } from 'vue'

var decodedText = ref('')



const onScan = (decodedText: any, decodedResult: any, html5QrcodeScanner: any) => {
  document.getElementById("html5-qrcode-button-camera-stop")?.click()
  alert(decodedText);
}

</script>

<template>

  <h1>Example 1</h1>
  <QRCodeScanner.default :qrbox="250" :fps="10" style="width: 500px;" @result="onScan" />

</template>

<style module>
video {
  max-width: 100% !important;
}
</style>