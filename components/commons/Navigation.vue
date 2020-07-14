<template>
  <header>
    <nav>
      <ul>
        <li>
          <nuxt-link to="/">
            {{ $t("navigation.homePage") }}
          </nuxt-link>
        </li>
        <li>
          <nuxt-link to="/freelance">
            {{ $t("navigation.freelance") }}
          </nuxt-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
header {
  position: absolute;
  width: 100%;
  height: 64px;
  nav {
    height: 100%;
  }
  ul {
    display: flex;
    height: 100%;
    align-items: center;
    a {
      display: block;
      position: relative;
      margin: 8px 16px;
      color: black;
      font-size: 1.2em;
      text-decoration: none;
      outline: none;

      &::after {
        content: "";
        position: absolute;
        width: 0;
        height: 2px;
        bottom: 0;
        left: 0;
        background-color: black;
        transition: width 0.3s;
      }
      &:hover,
      &:focus,
      &.nuxt-link-exact-active {
        &:after {
          width: 100%;
        }
      }
    }
  }
}
</style>
