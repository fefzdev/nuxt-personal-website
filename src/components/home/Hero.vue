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
export default {}
</script>

<style lang="scss" scoped>
.hero {
  position: relative;
  z-index: -1;

  display: flex;
  width: 100%;
  height: 100vh;
  min-height: 600px;
  padding-top: 80px;

  @media only screen and (min-width: 1px) and (max-width: 900px) {
    padding-top: 50px;
  }

  .inner--hero {
    position: relative;

    width: 100%;
    max-width: 100vw;
    margin: auto;

    text-align: center;

    > * {
      margin: 0 auto;
    }

    p {
      width: 90%;
      max-width: 700px;
      margin-bottom: 20px;

      font-size: 1.7em;

      @media only screen and (min-width: 1px) and (max-width: 900px) {
        font-size: 1.375em;
      }
    }

    .title {
      width: 90%;
      max-width: 1000px;
      margin-bottom: 40px;

      line-height: 1.1em;
    }
  }
}
</style>
