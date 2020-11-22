<template>
  <v-app>
    <Title />
    <v-main>
      <v-container>
        <v-card flat>
          <v-layout row>
            <div>
              <v-flex xs6 md3>
                <v-responsive></v-responsive>
              </v-flex>
              <v-flex xs6 md3>
                <v-card-text></v-card-text>
              </v-flex>
            </div>
          </v-layout>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Title from "./components/Title";

export default {
  name: "App",

  components: {
    Title,
  },

  data: () => ({
    //
  }),
};
</script>
