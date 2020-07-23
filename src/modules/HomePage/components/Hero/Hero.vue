<template>
  <section class="hero">
    <div class="inner--hero">
      <p lang="en">
        {{ data.hello }}
      </p>
      <Title :title-params="data.title" class="title" />
      <p class="desc">
        {{ data.subtitle }}
      </p>
      <p lang="en">
        {{ data.end_word }}
      </p>
    </div>
  </section>
</template>

<script>
import Title from '~/components/Title'

export default {
  components: {
    Title,
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
.hero {
  position: relative;
  z-index: -1;

  display: flex;
  width: 100%;
  height: 100vh;
  min-height: 600px;
  padding-top: 80px;

  @media only screen and (min-width: 1px) and (max-width: 900px) {
    padding-top: 50px;
  }

  .inner--hero {
    position: relative;

    width: 100%;
    max-width: 100vw;
    margin: auto;

    text-align: center;

    > * {
      margin: 0 auto;
    }

    p {
      width: 90%;
      max-width: 700px;
      margin-bottom: 20px;

      font-size: 1.7em;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        font-size: 1.375em;
      }
    }

    .title {
      margin-bottom: 40px;

      h1 {
        width: 90%;
        max-width: 1000px;

        line-height: 1.1em;
      }
    }
  }
}
</style>
