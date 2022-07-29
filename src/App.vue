<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link><br />
  </nav>
  {{nameTest}}
  <router-view />
</template>

<script>
export default {
  data() {
    return {
      nameTest: process.env.VUE_APP_NAME
    }
  }
}
</script>
<style lang="scss">
@import 'bootstrap';
</style>
