<template>
  <section class="story blk_bgr">
    <div class="inner">
      <div class="intro">
        <h2>
          {{ $t('storiesSection.title') }}
        </h2>
        <p class="section-description fadeIn">
          {{ $t('storiesSection.description') }}
        </p>
      </div>
      <div class="content">
        <div
          v-for="(story, index) in stories"
          :key="index"
          class="element fadeIn"
        >
          <div class="desc">
            <h3>{{ story.title }}</h3>
            <p
              v-for="(paragraph, paraId) in story.content"
              :key="paraId"
              class="regular-text section_content"
            >
              {{ paragraph }}
            </p>
          </div>
          <div class="view">
            <img
              :src="
                require(`~/assets/images/illustrations/${story.illustration}.png`)
              "
              :alt="story.altIllustration"
              loading="lazy"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      stories: this.$t('storiesSection.stories'),
    }
  },
}
</script>

<style lang="scss" scoped>
.story {
  .intro {
    max-width: 850px;
    margin: auto;
    margin-bottom: 130px;

    h2 {
      margin-bottom: 42px;
    }
  }

  .content {
    .element {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 90px;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        flex-direction: column !important;
      }

      &.jocus .view img,
      &.ipika .view img {
        width: 80%;
        margin: auto;
      }

      &:nth-child(2n) {
        flex-direction: row-reverse;
      }

      &:last-child {
        margin-bottom: 0;
      }

      .desc {
        width: 45%;

        @media only screen and (min-width: 1px) and (max-width: 900px) {
          width: 100%;
          margin-bottom: 30px;
        }

        h3 {
          width: 85%;
          margin-bottom: 30px;
        }

        p {
          margin-bottom: 30px;

          font-size: 1.5em;
          line-height: 1.48em;

          opacity: 0.7;

          &:last-child {
            margin-bottom: 0;
          }
        }
      }
      .view {
        width: 90%;

        @media (min-width: 600px) {
          width: 80%;
        }

        @media (min-width: 900px) {
          width: 45%;
        }

        img {
          display: block;
          width: 100%;
          height: auto;
        }
      }
    }
  }
}
</style>
