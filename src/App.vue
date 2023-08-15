<script setup>
import { ref } from 'vue'
import PreviewGallery from './components/PreviewGallery.vue'

const previewFileLinks = [
  'https://scandel.github.io/pdfThumbnails/example.pdf',
  'https://www.yummyday.com.tw/upload/5V/l1i/f03c6796549a4dc5b0fb1ca8633b636e.jpg',
  'https://mozilla.github.io/pdf.js/web/compressed.tracemonkey-pldi-09.pdf',
  'https://scandel.github.io/pdfThumbnails/example.pdf',
  'https://cdn.loveandlemons.com/wp-content/uploads/2023/01/tomato-soup.jpg',
  'https://mozilla.github.io/pdf.js/web/compressed.tracemonkey-pldi-09.pdf',
  'https://scandel.github.io/pdfThumbnails/example.pdf',
  'https://mozilla.github.io/pdf.js/web/compressed.tracemonkey-pldi-09.pdf',
]

const selectedLink = ref(previewFileLinks[0])

const handleSelect = (link) => {
  selectedLink.value = link
}
</script>

<template>
  <div class="container">
    <PreviewGallery
      :links="previewFileLinks"
      @show="handleSelect"
    />
    <div>
      {{ selectedLink }}
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
}
.previewer-wrapper {
  width: 20%;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
}
</style>
