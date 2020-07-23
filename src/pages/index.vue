<template>
  <HomePageModule :data="data" />
</template>

<script>
import HomePageModule from '~/modules/HomePage'

export default {
  name: 'HomePage',

  transition: 'default',

  components: {
    HomePageModule,
  },

  async asyncData({ $prismic, error }) {
    try {
      const data = (await $prismic.api.getSingle('homepage')).data
      return {
        data,
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Page not found' })
    }
  },
}
</script>
