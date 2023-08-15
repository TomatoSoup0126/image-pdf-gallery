<script setup>
import { computed } from 'vue'
import { isPdfLink } from '../utils/helper'
import PdfViewer from './PdfViewer.vue'
const props = defineProps({
  link: {
    type: String,
    default: ''
  }
})

const isPdf = computed(() => {
  return isPdfLink(props.link)
})
</script>

<template>
  <div class="viewer-container">
    <template v-if="isPdf">
      <PdfViewer :link="props.link" />
    </template>
    <template v-else>
      <div class="image-wrapper">
        <img
          class="image-item"
          :src="props.link"
        >
      </div>
    </template>
  </div>
</template>

<style scoped>
.viewer-container {
  width: 80%;
}
.image-wrapper {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.image-item {
  max-width:100%;
  max-height: 100%;
  object-fit: contain;
}
</style>