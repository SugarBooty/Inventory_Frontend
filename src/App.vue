<template>
  <v-app dark>
    <NavBar />

      <router-view></router-view>

  </v-app>
</template>

<script>
import NavBar from "@/components/NavBar.vue";

export default {
  name: "App",

  components: {
    NavBar,
  },

  data() {
    return {

    };
  },
  methods: {
    
  },
};
</script>

<style scoped></style>
