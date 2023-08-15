<script setup>
import { VuePDF, usePDF } from '@tato30/vue-pdf'

const props = defineProps({
  link: {
    type: String,
  }
})

const { pdf } = usePDF(props.link)

</script>

<template>
  <VuePDF
    :pdf="pdf"
    :page="1"
    :fit-parent="true"
  />
</template>

<style>
</style>