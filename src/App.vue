<template>
  <v-app>
    <Title />
    <Gallery />
  </v-app>
</template>

<script>
import Title from "./components/Title";
import Gallery from "./components/Gallery";
import Gallery from "./components/Gallery.vue";

export default {
  name: "App",

  components: {
    Title,
    Gallery,
  },

  data: () => ({
    //
  }),
};
</script>
