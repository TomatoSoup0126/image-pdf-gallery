<script setup>
import { VuePDF, usePDF } from '@tato30/vue-pdf'

const props = defineProps({
  link: {
    type: String,
    required: true
  }
})

const { pdf, pages } = usePDF(props.link)

</script>

<template>
  <div class="pdf-container">
    <div
      v-for="page in pages"
      :key="page"
      class="pdf-page"
    >
      <VuePDF
        :pdf="pdf"
        :page="page"
        :fit-parent="true"
      >
        <div>
          Loading...
        </div>
      </VuePDF>
    </div>
  </div>
</template>

<style>
.pdf-container {
  width: 100%;
  overflow-y: scroll;
  max-height: 90vh;
}
.pdf-page {
  margin-bottom: 1rem;
}
</style>