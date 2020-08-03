<template>
  <v-container>
    <v-row class="text-center">
      <v-col v-for="(e, i) in items" :key="i">
        <GridItem :title="e.title" :body="e.body" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import GridItem from "./GridItem";

export default {
  name: "Grid",

  components: { GridItem },

  data: () => ({
    items: null,
  }),

  mounted() {
    this.fetchItems();
  },

  methods: {
    fetchItems() {
      fetch("https://jsonplaceholder.typicode.com/posts")
        .then((stream) => stream.json())
        .then((data) => (this.items = data))
        .catch((error) => console.error(error));
    },
  },
};
</script>
