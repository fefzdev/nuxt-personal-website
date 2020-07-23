<template>
  <prismic-rich-text :field="textParams" />
</template>

<script>
export default {
  props: {
    textParams: {
      type: Array,
      required: true,
    },
  },
}
</script>

<style lang="scss" scoped></style>
