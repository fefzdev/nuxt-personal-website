<template>
  <main class="freelance">
    <section class="hello">
      <div class="inner">
        <h1>
          {{ $t('freelance.title') }}
        </h1>
        <i18n tag="p" path="freelance.description">
          <span slot="link">
            <nuxt-link to="/">
              {{ $t('freelance.linkDescription') }}
            </nuxt-link>
          </span>
        </i18n>
        <p>
          {{ $t('freelance.contactMe') }}
        </p>
      </div>
    </section>
  </main>
</template>

<style lang="scss" scoped>
.hello {
  padding-top: 64px;
  .inner {
    max-width: 700px;

    text-align: center;

    h1 {
      margin-bottom: 32px;
    }
    p {
      font-size: 1.3em;
      &:first-of-type {
        margin-bottom: 16px;
      }
      a {
        position: relative;

        color: black;
        text-decoration: none;

        outline: none;

        transition: color 0.2s;

        &::after {
          position: absolute;
          bottom: 0;
          left: -0.1em;
          z-index: -1;

          width: calc(100% + 0.1em);
          height: 2px;

          background-color: black;

          transition: height 0.2s;

          content: '';
        }
        &:hover,
        &:focus {
          color: white;
          &:after {
            height: 100%;
          }
        }
      }
    }
  }
}
</style>
