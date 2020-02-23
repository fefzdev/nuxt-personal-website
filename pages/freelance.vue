<template>
  <main class="freelance">
    <navigation />
    <section class="hello">
      <div class="inner">
        <h1>
          {{ $t('freelance.title') }}
        </h1>
        <i18n
          tag="p"
          path="freelance.description"
        >
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
    <mamy />
  </main>
</template>

<script>
import Navigation from '~/components/commons/navigation'
import Mamy from '~/components/home/Mamy'

export default {
  components: {
    Navigation,
    Mamy
  }
}
</script>

<style lang="scss" scoped>
.hello {
  padding-top: 64px;
  .inner {
    text-align: center;
    max-width: 700px;

    h1 {
      margin-bottom: 32px;
    }
    p {
      font-size: 1.3em;
      &:first-of-type {
        margin-bottom: 16px;
      }
      a {
        outline: none;
        position: relative;
        color: black;
        text-decoration: none;
        transition: color 0.2s;

        &::after {
          content: '';
          position: absolute;
          width: calc(100% + .1em);
          height: 2px;
          bottom: 0;
          left: -.1em;
          background-color: black;
          transition: height 0.2s;
          z-index: -1;
        }
        &:hover, &:focus {
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
