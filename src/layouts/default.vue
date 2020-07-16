<template>
  <div>
    <Navigation />
    <nuxt />
    <Mamy />
  </div>
</template>

<script>
import Navigation from "~/components/commons/Navigation";
import Mamy from "~/components/commons/Mamy";

export default {
  components: {
    Navigation,
    Mamy
  }
};
</script>
