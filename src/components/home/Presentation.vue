<template>
  <section class="presentation wht_bgr">
    <div class="inner">
      <h2>{{ $t('presentSection.title') }}</h2>
      <div class="fadeIn">
        <p class="section_desc">
          {{ $t('presentSection.description') }}
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
h2 {
  margin-bottom: 42px;
}
.presentation {
  .section_desc {
    margin-bottom: 40px;

    &:last-child {
      margin-bottom: 0;
    }
  }
}
</style>
