<script setup>
import { computed, ref } from 'vue'
import PreviewGallery from './components/PreviewGallery.vue'
import Viewer from './components/Viewer.vue'

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


const selectedIndex = ref(0)
const selectedLink = computed(() => previewFileLinks[selectedIndex.value])

const handleSelect = (index) => {
  selectedIndex.value = index
}
</script>

<template>
  <div class="container">
    <PreviewGallery
      :links="previewFileLinks"
      :selected-index="selectedIndex"
      @show="handleSelect"
    />
    <Viewer :link="selectedLink" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  max-height: 90vh;
  overflow: hidden;
}
.previewer-wrapper {
  width: 20%;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
}
</style>
