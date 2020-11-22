<template>
  <v-app>
    <Title />
    <v-main>
      <v-container>
        <Gallery />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Title from "./components/Title";
import Gallery from "./components/Gallery";

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
