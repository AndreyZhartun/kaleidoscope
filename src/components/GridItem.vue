<template>
  <v-container>
    <v-row class="text-center">
      <v-col>
        <h1 class="headline font-weight-bold mb-3">{{post.title}}</h1>

        <a :href="post.url" class="subheading font-weight-regular">{{post.url.split('/')[2]}}</a>
      </v-col>

      <!--<v-col class="mb-5" cols="12">
        <h2 class="headline font-weight-bold mb-3">What's next?</h2>

        <v-row justify="center">
          <a
            v-for="(next, i) in whatsNext"
            :key="i"
            :href="next.href"
            class="subheading mx-3"
            target="_blank"
          >{{ next.text }}</a>
        </v-row>
      </v-col>-->
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "GridItem",

  props: {
    id: {
      type: Number,
      required: true,
    },
    central: {
      type: Boolean,
    },
    /*body: {
      type: String,
      required: true,
    },*/
  },

  data: () => ({
    post: {
      title: "loading...",
      url: "//loading...",
    },
  }),

  mounted() {
    this.fetchPost();
  },

  methods: {
    fetchPost() {
      fetch("https://hacker-news.firebaseio.com/v0/item/" + this.id + ".json")
        .then((stream) => stream.json())
        .then((data) => (this.post = data))
        .catch((error) => console.error(error));
    },
  },
};
</script>
