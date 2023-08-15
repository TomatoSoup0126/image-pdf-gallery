<script setup>
import { defineEmits } from 'vue'
import PdfPreviewer from './PdfPreviewer.vue'
import { isPdfLink } from '../utils/helper'

const props = defineProps({
  links: {
    type: Array,
    required: true
  },
  selectedIndex: {
    type: Number,
  }
})

const emit = defineEmits(['show'])

const handleClick = (index) => {
  console.log('handleClick', index)
  emit('show', index)
}
</script>

<template>
  <div class="gallery-container">
    <div
      v-for="(link, index) in props.links"
      :key="link"
      class="gallery-item"
      :class="{ 'gallery-item--active': props.selectedIndex === index }"
      @click="handleClick(index)"
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
  border: 2px solid transparent;
}

.gallery-item--active {
  border: 2px solid rgb(250 204 21);;
}
</style>
