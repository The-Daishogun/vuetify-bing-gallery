<template>
  <v-app>
    <Title />
    <v-main>
      <v-container>
        <Jumbotron />
        <Gallery />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Title from "./components/Title";
import Gallery from "./components/Gallery";
import Jumbotron from "./components/Jumbotron";

export default {
  name: "App",

  components: {
    Title,
    Jumbotron,
    Gallery,
  },

  data: () => ({}),
};
</script>
