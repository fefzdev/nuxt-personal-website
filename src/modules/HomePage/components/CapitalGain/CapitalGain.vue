<template>
  <section class="capital_gain blk_bgr">
    <div class="inner">
      <div
        v-for="(element, elementIndex) in data"
        :key="elementIndex"
        class="element"
      >
        <div class="desc fadeIn">
          <h2>{{ element.title[0].text }}</h2>

          <RichText :text-params="element.subtitle" class="section_content" />
        </div>
        <div class="view checkFadeIn">
          <div class="bgr" />
          <div class="content">
            <Title :title-params="element.card_title" class="card_title" />
            <ul class="list">
              <li
                v-for="(item, itemIndex) in element.card_item"
                :key="itemIndex"
                :class="
                  item.card_item_is_checked ? 'need-check' : 'item--unchecked'
                "
                class="item"
              >
                {{ item.card_item_text }}
                <span class="check">
                  <img
                    loading="lazy"
                    svg-inline
                    src="~/assets/images/icons/check.svg"
                    alt="check icon"
                  />
                </span>
              </li>
            </ul>
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
      capitalElements: this.$t('capitalSection.elements'),
    }
  },
}
</script>

<style lang="scss" scoped>
.capital_gain {
  .element {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 130px;

    @media only screen and (min-width: 1px) and (max-width: 900px) {
      flex-direction: column;
    }

    &:last-child {
      margin-bottom: 0;
    }

    &:nth-child(n + 2) {
      flex-direction: row-reverse;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        flex-direction: column;
      }
    }

    &:nth-child(n + 2) .view {
      right: inherit;
      left: 10px;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        right: 10px;
        left: inherit;
      }
    }

    &:nth-child(n + 2) .view__bgr::before {
      left: -26px;
    }

    /* desc */
    .desc {
      width: 50%;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        width: 100%;
        margin-bottom: 30px;
      }

      h2 {
        width: 90%;
        margin-bottom: 20px;

        font-size: 3em;

        @media only screen and (min-width: 1px) and (max-width: 900px) {
          width: 100%;
        }
      }

      h2,
      p {
        text-align: left;
      }

      p {
        margin-bottom: 20px;

        opacity: 0.7;

        &:last-child {
          margin-bottom: 0;
        }
      }
    }
    .view {
      position: relative;
      right: 10px;

      width: 50%;
      max-width: 380px;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        width: 90%;
      }

      .content,
      .bgr {
        width: 100%;
      }
      .content {
        position: relative;
        z-index: 1;

        height: auto;
        padding: 40px;

        color: #000;

        @media only screen and (min-width: 1px) and (max-width: 900px) {
          padding: 35px;
        }

        .card_title {
          margin-bottom: 30px;
          padding-bottom: 30px;
          border-bottom: 1px solid #c4c4c440;

          @media only screen and (min-width: 1px) and (max-width: 900px) {
            margin-bottom: 25px;
            padding-bottom: 20px;
          }
        }

        .list {
          height: 100%;

          font-size: 1.5em;
          line-height: 1.1em;

          @media only screen and (min-width: 1px) and (max-width: 900px) {
            font-size: 1.25em;
          }

          .item {
            position: relative;

            margin-bottom: 30px;
            padding-left: 40px;

            &:last-child {
              margin-bottom: 0;
            }

            span {
              position: absolute;
              top: 50%;
              left: 0;

              width: 24px;
              height: 24px;
              border: solid 1px #e4e4e4;
              border-radius: 4px;
              overflow: hidden;

              transform: translateY(-50%);

              transition: ease 0.3s;

              svg {
                position: absolute;
                top: 50%;
                left: 50%;

                transform: translate(-50%, -50%);

                path {
                  transform: translateY(-10%);
                }
              }

              &::before {
                position: absolute;
                top: 50%;
                left: 50%;

                width: 24px;
                height: 24px;

                background-color: #0099ff;

                transform: translate(-50%, -50%) scale(0);

                transition: transform 0.3s;

                content: '';
              }
            }
          }
        }
      }

      &.check-animate {
        .content .list {
          @for $spanNumber from 1 through 5 {
            .need-check:nth-child(#{$spanNumber}) span {
              animation: shadowAnimation 0.3s 0.3s * $spanNumber;

              &::before {
                transform: translate(-50%, -50%) scale(1);

                transition-delay: 0.3s * $spanNumber;
              }

              svg {
                stroke-dasharray: 0, 1000;

                animation: svgCheckAnimation 0.3s ease-out forwards;
                animation-delay: 0.3s * $spanNumber + 0.2s;
              }
            }
          }
        }

        .content .list .item.item--unchecked span::before {
          content: none;
        }
      }
    }
  }
}

@keyframes svgCheckAnimation {
  0% {
    stroke-dasharray: 0, 1000;
  }
  to {
    stroke-dasharray: 20, 1000;
  }
}
@keyframes shadowAnimation {
  from {
    box-shadow: 0 0 0 0 white, 0 0 0 4px #0099ff;
  }
  to {
    box-shadow: 0 0 0 6px white, 0 0 0 6px #0099ff;
  }
}

/* view background*/
.bgr {
  position: absolute;
  z-index: 0;

  height: 100%;

  &::before,
  &::after {
    position: absolute;
    top: 25px;
    left: 26px;

    width: 100%;
    height: 100%;
    border-radius: 5px;

    background-color: #fff;

    content: '';
  }
  &::after {
    top: 0;
    left: 0;

    box-shadow: 0px 4px 20px #00000025;
  }
}
</style>
