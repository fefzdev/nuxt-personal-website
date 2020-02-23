<template>
  <a href="mailto:bouveret.felix@gmail.com" class="contact">
    <div class="title">
      <p lang="en">Let's talk</p>
      <p>bouveret.felix@gmail.com</p>
    </div>
  </a>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.contact {
  display: block;
  text-align: center;
  text-decoration: none;
  color: #fff;
  background: url(~assets/images/bgr_mamie.webp) center 44% / cover no-repeat black;

  &:hover .title, &:focus .title {
    text-decoration: underline;
  }

  @media (min-width: 720px) {
    outline: 0;
    &:hover .title, &:focus .title {
      background-color: rgba(0, 0, 0, .7);
    }
  }

  .title {
    padding: 160px 0;
    background-color: rgba(0, 0, 0, .7);
    transition: background-color 0.3s;
    line-height: 1.23em;
    font-size: 8vw;

    @media (min-width: 720px) {
      font-size: 3.1em;
      background-color: rgba(0, 0, 0, 1);
    }
  }
}
</style>
