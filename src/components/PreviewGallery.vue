<script setup>
import { defineEmits } from 'vue'
import PdfPreviewer from './PdfPreviewer.vue'
import { isPdfLink } from '../utils/helper'

const props = defineProps({
  links: {
    type: Array,
    required: true
  }
})

const emit = defineEmits(['show'])

const handleClick = (link) => {
  emit('show', link)
}
</script>

<template>
  <div class="gallery-container">
    <div
      class="gallery-item"
      v-for="link in props.links"
      :key="link"
      @click="handleClick(link)"
    >
      <div
        v-if="!isPdfLink(link)"
        :style="{ backgroundImage: `url(${link})` }"
        class="gallery-image"
      />
      <div
        v-else
        class="gallery-pdf"
      >
        <PdfPreviewer :link="link" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.gallery-container {
  max-height: 90vh;
  width: 20%;
  overflow-y: scroll;
  padding-right: 1rem;
}

.gallery-image {
  width: 100%;
  padding-top: 100%;
  background-size: cover;
  background-position: center;
}

.gallery-pdf {
  max-width: 100%;
}

.gallery-item {
  margin-bottom: 1rem;
  cursor: pointer;
}
</style>
