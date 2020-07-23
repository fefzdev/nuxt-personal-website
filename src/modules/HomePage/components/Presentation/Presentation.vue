<template>
  <section class="presentation wht_bgr">
    <div class="inner">
      <Title :title-params="data.title" class="title" />
      <RichText :text-params="data.subtitle" class="fadeIn section_desc" />
    </div>
  </section>
</template>

<script>
import Title from '~/components/Title'
import RichText from '~/components/RichText'

export default {
  components: {
    Title,
    RichText,
  },

  props: {
    data: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style lang="scss" scoped>
.title {
  margin-bottom: 42px;
}
</style>
