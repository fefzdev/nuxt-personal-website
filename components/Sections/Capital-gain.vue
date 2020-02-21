<template>
  <section class="capital_gain blk_bgr">
    <div class="inner">

      <div
        v-for="(element, elementIndex) in capitalElements"
        :key="elementIndex"
        class="element"
      >
        <div class="desc fadeIn">
          <h2>{{ element.title }}</h2>
          <p
            v-for="(description, descIndex) in element.descriptions"
            :key="descIndex"
            class="section_content"
          >
            {{ description }}
          </p>
        </div>
        <div class="view checkFadeIn1">
          <div class="bgr"></div>
          <div class="content">
            <h3>{{ element.subTitle }}</h3>
            <ul class="list">
              <li
                v-for="(item, itemIndex) in element.list"
                :key="itemIndex"
                class="item"
                :class="item.check ? 'need-check' : 'item--unchecked'"
              >
                {{ item.desc }}
                <span class="check">
                  <img svg-inline src="~/assets/images/icons/check.svg" alt="check icon">
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
export default {
  data () {
    return {
      capitalElements: this.$t('capitalSection.elements')
    }
  }
}
</script>

<style lang="scss" scoped>
.capital_gain {
  .element {
    display: flex;
    justify-content: space-between;
    align-items: center;
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
        font-size: 3em;
        margin-bottom: 20px;
        width: 90%;

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
      max-width: 380px;
      width: 50%;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        width: 90%;
      }

      .content,
      .bgr {
        width: 100%;
      }
      .content {
        height: auto;
        padding: 40px;
        position: relative;
        z-index: 1;
        color: #000;

        @media only screen and (min-width: 1px) and (max-width: 900px) {
          padding: 35px;
        }

        h3 {
          margin-bottom: 30px;
          padding-bottom: 30px;
          border-bottom: 1px solid #c4c4c440;

          @media only screen and (min-width: 1px) and (max-width: 900px) {
            margin-bottom: 25px;
            padding-bottom: 20px;
          }
        }

        .list {
          font-size: 1.5em;
          line-height: 1.1em;
          height: 100%;

          @media only screen and (min-width: 1px) and (max-width: 900px) {
            font-size: 1.25em;
          }

          .item {
            position: relative;
            padding-left: 40px;
            margin-bottom: 30px;

            &:last-child {
              margin-bottom: 0;
            }

            span {
              position: absolute;
              width: 24px;
              height: 24px;
              left: 0;
              top: 50%;
              transform: translateY(-50%);
              transition: ease 0.3s;
              border: solid 1px #e4e4e4;
              border-radius: 4px;
              overflow: hidden;
              svg {
                transform: translate(-50%, -50%);
                top: 50%;
                left: 50%;
                position: absolute;

                path {
                  transform: translateY(-10%);
                }
              }

              &::before {
                content: '';
                position: absolute;
                width: 24px;
                height: 24px;
                background-color: #0099FF;
                transform: translate(-50%, -50%) scale(0);
                top: 50%;
                left: 50%;
                transition: transform .3s;
              }

              &.check-animate {

                &::before {
                  transform: translate(-50%, -50%) scale(1);
                }

                svg {
                  stroke-dasharray: 0, 1000;
                  animation: svgCheckAnim 0.3s ease-out forwards;
                  animation-delay: 0.3s;
                }
              }
            }
          }
        }
      }

      &.check-animate {
        .content .list {
          @for $spanNumber from 1 through 5 {
            .need-check:nth-child(#{$spanNumber}) span {

              &::before {
                transform: translate(-50%, -50%) scale(1);
                transition-delay: 0.3s*$spanNumber;
              }

              svg {
                stroke-dasharray: 0, 1000;
                animation: svgCheckAnim 0.3s ease-out forwards;
                animation-delay: 0.3s * $spanNumber + .2s;
              }
            }
          }
        }

        .content .list .item.item--unchecked span::before {
          content:none;
        }
      }
    }
  }
}

@keyframes svgCheckAnim {
  0% {
    stroke-dasharray: 0, 1000;
  }
  to {
    stroke-dasharray: 20, 1000;
  }
}

/* view background*/
.bgr {
  position: absolute;
  z-index: 0;
  height: 100%;
  &::before, &::after {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    background: #fff;
    border-radius: 5px;
    left: 26px;
    top: 25px;
  }
  &::after {
    left: 0;
    top: 0;
    box-shadow: 0px 4px 20px #00000025;
  }
}
</style>
