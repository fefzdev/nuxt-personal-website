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
          class="content__element fadeIn"
        >
          <div class="content__element__desc">
            <h3>{{ story.title }}</h3>
            <p
              v-for="(paragraph, paraId) in story.content"
              :key="paraId"
              class="regular-text section_content"
            >
              {{ paragraph }}
            </p>
            <img :src="require(`~/assets/images/illustrations/${story.illustration}.png`)" :alt="story.altIllustration">
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      stories: this.$t('storiesSection.stories')
    }
  }
}
</script>

<style lang="scss" scoped>

.story {
  background-color: black;
  color: white;
  padding: 50px 0;
}
.intro {
  margin-bottom: 130px;
}

.content__element {
  display: flex;
  justify-content: space-between;
  margin-bottom: 90px;
  align-items: center;
}
.content__element.jocus .content__element__view img, .content__element.ipika .content__element__view img {
  width: 80%;
  margin: auto;
}
.content__element:nth-child(2n) {
  flex-direction: row-reverse;
}
.content__element:last-child {
  margin-bottom: 0;
}
.content__element__desc {
  width: 45%;
}
.content__element__desc h3 {
  width: 85%;
  margin-bottom: 30px;
}
.content__element__desc p {
  opacity: 0.7;
  line-height: 1.48em;
  margin-bottom: 30px;
}
.content__element__desc p:last-child {
  margin-bottom: 0;
}

.content__element__view {
  width: 45%;
}
.content__element__view img {
  width: 100%;
  height: auto;
  display: block;
}
</style>
