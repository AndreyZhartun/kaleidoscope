<template>
  <v-app>
    <AppBar />
    <v-main>
      <Grid />
    </v-main>
  </v-app>
</template>

<script>
import Grid from "./components/Grid";
import AppBar from "./components/AppBar";

export default {
  name: "App",

  components: {
    Grid,
    AppBar,
  },

  data: () => ({
    //
  }),
};
</script>
