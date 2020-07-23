<template>
  <prismic-rich-text :field="titleParams" :class="additionalClass" />
</template>

<script>
export default {
  props: {
    titleParams: {
      type: Array,
      required: true,
    },
    additionalClass: {
      type: String,
      default: null,
    },
  },
}
</script>

<style></style>
