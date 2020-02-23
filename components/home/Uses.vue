<template>
  <section class="uses blk_bgr">
    <div class="inner">
      <div class="intro">
        <h2>{{ $t('usesSection.title') }}</h2>
        <p class="section_desc fadeIn">
          {{ $t('usesSection.description') }}
        </p>
      </div>
      <div class="content">
        <div class="windows_container">
          <div
            v-for="(window, windowIndex) in windows"
            :key="windowIndex"
            class="window"
          >
            <div class="header">
              <div class="dots">
                <span />
                <span />
                <span />
              </div>
              <p class="title">
                {{ window.title }}.html
              </p>
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
                  //--------{{ window.title }}------------
                </p>
                <div class="infos">
                  <p>
                    <span>var </span>{{ window.title }}
                  </p>
                  <ul class="info_list">
                    <li
                      v-for="(item, itemIndex) in window.list"
                      :key="itemIndex"
                      class="item"
                    >
                      '{{ item }}'
                    </li>
                  </ul>
                </div>
                <p v-if="window.info" class="comments">
                  {{ window.info }}
                </p>
                <span class="script_bls script_bls--close">script</span>
              </div>
            </div>
          </div>
        </div>

        <div class="logos_container">
          <ul class="logo_list">
            <li
              v-for="(logo, logoIndex) in logoList"
              :key="logoIndex"
              class="item"
            >
              <img :src="require(`assets/images/software_logos/${logo.image}`)" :alt="logo.imageAlt" class="item__img">
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      windows: this.$t('usesSection.windows'),
      logoList: this.$t('usesSection.logoList')
    }
  }
}
</script>

<style lang="scss" scoped>
.uses {
  .intro {
    h2 {
      margin-bottom: 42px;
    }
    .section_desc {
      margin-bottom: 50px;
    }
  }
}

.windows_container {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  margin-bottom: 30px;

  .window {
    width: 330px;
    height: 100%;
    min-height: 380px;
    background-color: #1c1c1c;
    margin: 0 1em 30px;
    border-radius: 5px;
    transition: ease 0.3s;

    &:last-child {
      margin-bottom: 0;
    }

    .header {
      width: 100%;
      height: 35px;
      position: relative;
      background-color: #222222;
      border-radius: 5px 5px 0 0;

      .title {
        text-align: center;
        line-height: 35px;
        font-size: 12px;
        color: #777777;
      }

      .dots {
        position: absolute;
        width: auto;
        height: 8px;
        transform: translateY(-50%);
        top: 50%;
        left: 10px;
        display: flex;

        span {
          width: 8px;
          height: 8px;
          border-radius: 200px;
          margin-left: 5px;
          display: block;

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
      padding: 15px;
      display: flex;
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
          display: block;
          color: #ff4a45;
          position: relative;
          padding-left: 0.6em;

          &::before {
            content: "<";
            position: absolute;
            color: #ffffff90;
            left: 0;
          }

          &::after {
            content: ">";
            position: absolute;
            color: #ffffff90;
          }

          &.script_bls--close {
            padding-left: 1em;

            &::before {
              content: "</";
            }
          }
        }

        .comments {
          color: #ffffff80;
          font-style: italic;
        }

        .infos {
          margin: 23px 0;

          p {
            display: inline;
            color: #0099ff;
            position: relative;
            padding-right: 1em;

            &::after {
              content: "=";
              position: absolute;
              color: #eb70e6;
              right: 0.5em;
            }
          }

          span {
            color: #6cd5ff;
          }

          .info_list {
            display: inline;
            position: relative;

            &::before {
              content: "[";
              position: absolute;
              transform: translateX(-100%);
            }

            &::after {
              content: "];";
              position: relative;
            }

            .item {
              display: inline;
              color: #98ed66;

              &::after {
                content: ",";
                color: #fff;
              }

              &:last-child::after {
                content: "";
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
    justify-content: space-around;
    align-items: center;
    flex-wrap: wrap;

    .item {
      display: block;
    }
  }
}
</style>
