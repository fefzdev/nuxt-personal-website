<template>
  <section class="likes blk_bgr">
    <div class="inner">
      <h2>{{ $t('likesSection.title') }}</h2>
      <div class="content">
        <article
          v-for="(like, likeIndex) in likes"
          :key="likeIndex"
          class="element love_dev fadeIn"
        >
          <img :src="require(`assets/images/icons/${like.image}.svg`)" :alt="like.imageAlt">
          <h4>{{ like.title }}</h4>
          <!-- eslint-disable-next-line -->
          <p v-html="like.description" />
        </article>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      likes: this.$t('likesSection.likes')
    }
  }
}
</script>

<style lang="scss" scoped>
.likes {
  h2 {
    margin-bottom: 80px;
  }
  .content {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;

    @media only screen and (min-width: 1px) and (max-width: 600px) {
      flex-direction: column;
    }

    .element {
      min-width: 350px;
      flex: 1;
      margin: 10px 10px 0;
      position: relative;
      padding-top: 52px;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        margin-bottom: 30px;

        &:last-child {
          margin-bottom: 0;
        }
      }

      @media only screen and (min-width: 1px) and (max-width: 600px) {
        min-width: 0;
      }

      img {
        width: 32px;
        height: 32px;
        margin-bottom: 10px;
      }

      h4 {
        margin-bottom: 20px;
      }

      p {
        font-size: 1.375em;
        line-height: 1.49em;
        opacity: 0.7;
      }
    }
  }
}
</style>
