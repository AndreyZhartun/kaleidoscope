<template>
  <v-app-bar app color="#46433A" dark dense>
    <div class="d-flex align-center">
      <v-icon>mdi-view-grid</v-icon>&nbsp;&nbsp;&nbsp;&nbsp;
      <span>kaleidoscope</span>

      <v-btn href="https://github.com/AndreyZhartun/kaleidoscope" target="_blank" text>
        <v-icon>mdi-github</v-icon>
        <!--<span class="mr-1">Github</span>-->
        <span>Github</span>
      </v-btn>

      <v-btn href="https://andreyzhartun.github.io" target="_blank" text>
        <v-icon>mdi-card-account-details</v-icon>
        <span>Про меня</span>
      </v-btn>
    </div>

    <v-spacer></v-spacer>

    <span>Vuetify, ...</span>
  </v-app-bar>
</template>

<script>
export default {
  name: "AppBar",
};
</script>

<style scoped>
</style>