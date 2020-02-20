<template>
  <div>
    <hero-section />
    <stories-section />
  </div>
</template>

<script>
import HeroSection from '~/components/Sections/Hero'
import StoriesSection from '~/components/Sections/Stories'

export default {
  components: {
    HeroSection,
    StoriesSection
  }
}
</script>

<style lang="scss" scoped>

</style>
