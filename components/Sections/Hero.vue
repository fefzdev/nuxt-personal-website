<template>
  <section class="hero">
    <div class="inner--hero">
      <p lang="en">
        {{ $t('heroSection.hello') }}
      </p>
      <h1 class="title">
        {{ $t('heroSection.title') }}
      </h1>
      <p class="desc">
        {{ $t('heroSection.description') }}
      </p>
      <p lang="en">
        {{ $t('heroSection.intro') }}
      </p>
    </div>
  </section>
</template>

<script>
export default {
  mounted () {
    const resizeEvent = () => {
      return window.innerHeight ||
        document.documentElement.clientHeight ||
        document.body.clientHeight
    }

    const hero = document.querySelector('.hero')
    const inner = document.querySelector('.inner--hero')

    const parralax = (element, speed) => {
      const topPage = window.pageYOffset
      const bottomParallaxElement = element.scrollHeight
      const pourcent = (topPage * 100 / bottomParallaxElement) / speed * -1
      const containerEnd = hero.offsetTop + hero.clientHeight

      if (resizeEvent() > 600 && topPage < containerEnd) {
        element.style.top = 'calc(' + topPage + 'px + ' + pourcent + '%)'
      } else {
        element.style.top = ''
      }
    }

    window.onscroll = () => parralax(inner, 5)
    window.onresize = () => parralax(inner, 5)
  }
}
</script>

<style lang="scss" scoped>
.hero {
  position: relative;
  display: flex;
  width: 100%;
  height: 100vh;
  min-height: 600px;
  padding-top: 80px;

  @media only screen and (min-width: 1px) and (max-width: 900px) {
    padding-top: 50px;
  }

  .inner--hero {
    max-width: 100vw;
    width: 100%;
    text-align: center;
    position: relative;
    margin: auto;

    > * {
      margin: 0 auto;
    }

    p {
      font-size: 1.7em;
      max-width: 700px;
      width: 90%;
      margin-bottom: 20px;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        font-size: 1.375em;
      }
    }

    .title {
      line-height: 1.1em;
      margin-bottom: 40px;
      max-width: 1000px;
      width: 90%;
    }
  }
}
</style>
