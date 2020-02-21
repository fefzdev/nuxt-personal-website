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
  font-size: 3.1em;
  line-height: 1.23em;
  color: #fff;
  background: url(~assets/images/bgr_mamie.gif) center 44% / cover no-repeat black;

  .title {
    padding: 160px 0;
    background: rgba(0, 0, 0, 1);
    transition: all 0.3s;

    @media only screen and (min-width: 1px) and (max-width: 900px) {
      font-size: 8vw;
    }

    &:hover {
      background-color: rgba(0, 0, 0, .7);
    }
  }
}
</style>
