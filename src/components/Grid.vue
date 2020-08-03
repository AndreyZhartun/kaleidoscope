<template>
  <v-container v-if="allPosts !== null">
    <v-row class="text-center">
      <v-col
        cols="4"
        v-for="(e, j) in allPosts.slice(centralIndex - gridSize - 1, centralIndex - gridSize + 2)"
        :key="j"
      >
        <GridItem :id="e" />
      </v-col>
    </v-row>
    <v-row class="text-center">
      <v-col cols="3">
        <GridItem :id="allPosts[centralIndex-1]" />
      </v-col>
      <v-col cols="6">
        <GridItem :id="allPosts[centralIndex]" />
      </v-col>
      <v-col cols="3">
        <GridItem :id="allPosts[centralIndex+1]" />
      </v-col>
    </v-row>
    <v-row class="text-center">
      <v-col
        cols="4"
        v-for="(e, j) in allPosts.slice(centralIndex + gridSize - 1, centralIndex + gridSize + 2)"
        :key="j"
      >
        <GridItem :id="e" />
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
    allPosts: null,
    gridSize: null,
    centralIndex: null,
  }),

  mounted() {
    this.fetchTopPosts();
  },

  methods: {
    fetchTopPosts() {
      fetch("https://hacker-news.firebaseio.com/v0/topstories.json")
        .then((stream) => stream.json())
        .then((data) => {
          this.allPosts = data;
          // Нахождение индекса центрального поста:
          //   data - 1-мерный массив, для сетки удобнее работать с ним как с 2-мерным.
          //   Находим кв. корень из длины data - длина data === size*size + остаток
          this.gridSize = Math.floor(Math.sqrt(this.allPosts.length));
          //   Центральный пост в матрице [size/2][size/2] или в 1-мерном массиве:
          this.centralIndex =
            this.gridSize * Math.ceil(this.gridSize / 2) +
            Math.ceil(this.gridSize / 2);
          console.log(
            "len is " +
              this.allPosts.length +
              ", gridSize is " +
              this.gridSize +
              ", cI is " +
              this.centralIndex
          );
        })
        .catch((error) => console.error(error));
    },
  },
};
</script>
