<template>
  <div class="header">
    <nuxt-link to="/" exact>Home</nuxt-link>
    <nuxt-link to="/about">About</nuxt-link>
    <nuxt-link v-if="$auth.loggedIn" to="/secret">Top Secret</nuxt-link>
    <a
      href="https://inklud.eu.auth0.com/v2/logout?returnTo=https://app.covidu.com&client_id=eEymJzS3Dmn9nnEhqhD0woAgyE6NLCbS"
      v-if="$auth.loggedIn"
      @click="$auth.logout()"
    >Sign Off</a>
    <a v-else @click="$auth.loginWith('auth0')">Sign In</a>
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  computed: mapGetters(["isAuthenticated"])
};
</script>

<style scoped>
.header {
  display: flex;
  margin-bottom: 20px;
}
a {
  margin-right: 20px;
  font-size: 14px;
  color: #999;
  text-decoration: none;
  text-transform: uppercase;
  padding-top: 2px;
  padding-bottom: 2px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  transition: color 0.25s;
  font-weight: 400;
  line-height: normal;
  cursor: pointer;
}
a:hover {
  color: #333;
}
a.nuxt-link-active {
  color: #333;
  border-top: 1px solid #333;
  border-bottom: 1px solid #333;
  font-weight: 600;
}
</style>
