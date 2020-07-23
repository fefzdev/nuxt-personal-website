<template>
  <section class="uses blk_bgr">
    <div class="inner">
      <div class="intro">
        <Title :title-params="data.title" class="title" />
        <p class="section_desc fadeIn">
          {{ data.subtitle }}
        </p>
      </div>
      <div class="content">
        <div class="windows_container">
          <div
            v-for="(window, windowIndex) in data.windows"
            :key="windowIndex"
            class="window"
          >
            <div class="header">
              <div class="dots">
                <span />
                <span />
                <span />
              </div>
              <p class="title">{{ window.primary.window_name }}.html</p>
            </div>
            <div class="content">
              <div class="lines">
                <span v-for="(i, index) in 14" :key="index">
                  {{ index + 1 }}
                </span>
              </div>
              <div class="text">
                <span class="script_bls">script</span>
                <p class="comments">
                  //--------{{ window.primary.window_name }}------------
                </p>
                <div class="infos">
                  <p><span>var </span>{{ window.primary.window_name }}</p>
                  <ul class="info_list">
                    <li
                      v-for="(item, itemIndex) in window.items"
                      :key="itemIndex"
                      class="item"
                    >
                      '{{ item.window_item }}'
                    </li>
                  </ul>
                </div>
                <p v-if="window.info" class="comments">
                  {{ window.primary.window_comment }}
                </p>
                <span class="script_bls script_bls--close">script</span>
              </div>
            </div>
          </div>
        </div>

        <div class="logos_container">
          <ul class="logo_list">
            <li
              v-for="(logo, logoIndex) in data.logo_list"
              :key="logoIndex"
              class="item"
            >
              <img
                :src="logo.tool_logo.url"
                :alt="logo.tool_logo.alt"
                loading="lazy"
                class="item__img"
              />
            </li>
          </ul>
        </div>
      </div>
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
.title {
  margin-bottom: 42px;
}

.section_desc {
  margin-bottom: 50px;
}

.windows_container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  margin-bottom: 30px;

  .window {
    width: 330px;
    height: 100%;
    min-height: 380px;
    margin: 0 1em 30px;
    border-radius: 5px;

    background-color: #1c1c1c;

    transition: ease 0.3s;

    &:last-child {
      margin-bottom: 0;
    }

    .header {
      position: relative;

      width: 100%;
      height: 35px;
      border-radius: 5px 5px 0 0;

      background-color: #222222;

      .title {
        color: #777777;
        font-size: 12px;
        line-height: 35px;
        text-align: center;
      }

      .dots {
        position: absolute;
        top: 50%;
        left: 10px;

        display: flex;
        width: auto;
        height: 8px;

        transform: translateY(-50%);

        span {
          display: block;
          width: 8px;
          height: 8px;
          margin-left: 5px;
          border-radius: 200px;

          &:first-child {
            margin: 0;
          }

          &:nth-child(1) {
            background-color: #fc605c;
          }

          &:nth-child(2) {
            background-color: #fdbc40;
          }

          &:nth-child(3) {
            background-color: #35c94a;
          }
        }
      }
    }

    .content {
      display: flex;
      padding: 15px;

      font-size: 16px;
      line-height: 23px;

      .lines {
        text-align: right;
      }

      .lines span {
        display: block;
      }

      .text {
        flex: 1;
        padding-left: 10px;

        .script_bls {
          position: relative;

          display: block;
          padding-left: 0.6em;

          color: #ff4a45;

          &::before {
            position: absolute;
            left: 0;

            color: #ffffff90;

            content: '<';
          }

          &::after {
            position: absolute;

            color: #ffffff90;

            content: '>';
          }

          &.script_bls--close {
            padding-left: 1em;

            &::before {
              content: '</';
            }
          }
        }

        .comments {
          color: #ffffff7a;
          font-style: italic;
        }

        .infos {
          margin: 23px 0;

          p {
            position: relative;

            display: inline;
            padding-right: 1em;

            color: #0099ff;

            &::after {
              position: absolute;
              right: 0.5em;

              color: #eb70e6;

              content: '=';
            }
          }

          span {
            color: #6cd5ff;
          }

          .info_list {
            position: relative;

            display: inline;

            &::before {
              position: absolute;

              transform: translateX(-100%);

              content: '[';
            }

            &::after {
              position: relative;

              content: '];';
            }

            .item {
              display: inline;

              color: #98ed66;

              &::after {
                color: #fff;

                content: ',';
              }

              &:last-child::after {
                content: '';
              }
            }
          }
        }
      }
    }
  }
}

.logos_container {
  width: 100%;

  .logo_list {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-around;

    .item {
      display: block;
    }
  }
}
</style>
