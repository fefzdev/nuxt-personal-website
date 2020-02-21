<template>
  <div>
    <hero-section />
    <stories-section />
    <likes-section />
    <uses-section />
    <pres-section />
    <capital-section />
    <mamy />
  </div>
</template>

<script>
import HeroSection from '~/components/Sections/Hero'
import StoriesSection from '~/components/Sections/Stories'
import LikesSection from '~/components/Sections/Likes'
import UsesSection from '~/components/Sections/Uses'
import PresSection from '~/components/Sections/Presentation'
import CapitalSection from '~/components/Sections/Capital-gain'
import Mamy from '~/components/Sections/Mamy'

export default {
  components: {
    HeroSection,
    StoriesSection,
    LikesSection,
    UsesSection,
    PresSection,
    CapitalSection,
    Mamy
  }
}
</script>

<style lang="scss" scoped>

</style>
