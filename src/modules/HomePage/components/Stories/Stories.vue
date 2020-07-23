<template>
  <section class="story blk_bgr">
    <div class="inner">
      <div class="intro">
        <Title :title-params="data.title" class="title" />

        <p class="section-description fadeIn">
          {{ data.subtitle }}
        </p>
      </div>
      <div class="content">
        <div
          v-for="(story, index) in data.stories"
          :key="index"
          class="element fadeIn"
        >
          <div class="desc">
            <Title :title-params="story.story_title" class="story_title" />

            <RichText
              :text-params="story.story_description"
              class="regular-text"
            />
          </div>
          <div class="view">
            <img
              :src="story.story_image.url"
              :alt="story.story_image.alt"
              loading="lazy"
            />
          </div>
        </div>
      </div>
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
  }

  .title {
    margin-bottom: 42px;
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

        .story_title {
          width: 85%;
          margin-bottom: 30px;
        }

        .regular-text {
          color: #b2b2b2;
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
