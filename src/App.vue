<template>
  <v-app>
    <router-link to="Home"></router-link>
    <router-view />
  </v-app>
</template>

<script>
import Home from './views/Home'
export default {
  name: "App",

  components: {
    Home,
  },

  data: () => ({
    //
  }),
};
</script>
