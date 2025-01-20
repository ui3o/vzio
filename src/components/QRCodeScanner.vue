<script lang="ts">
import { defineComponent } from 'vue';

var html5QrcodeScanner: any;

export default defineComponent({
  props: {
    qrbox: {
      type: Number,
      default: 250
    },
    fps: {
      type: Number,
      default: 10
    },
  },
  mounted() {
    const config = {
      fps: this.fps,
      qrbox:  { width: 250, height: 150 } ,
    };
    // @ts-ignore
    html5QrcodeScanner = new Html5QrcodeScanner('qr-code-full-region', config);
    // @ts-ignore
    html5QrcodeScanner.render(this.onScanSuccess);

  },
  methods: {
    onScanSuccess(decodedText: any, decodedResult: any) {
      this.$emit('result', decodedText, decodedResult, html5QrcodeScanner);
    }
  }
})
</script>

<template>
  <div id="qr-code-full-region"></div>
</template>

<style scoped>
#qr-code-full-region {
  width: 100% !important;
}
</style>