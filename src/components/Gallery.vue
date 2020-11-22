<template>
  <v-main>
    <v-container>
      <v-card flat>
        <v-layout row>
          <div v-for="img in imgs" :key="img.id">
            <v-flex xs6 md3>
              <v-responsive>
                <img :src="`${img.url}`" alt="" />
              </v-responsive>
            </v-flex>
            <v-flex xs6 md3>
              <v-card-text class="float-right">
                <h1 class="subtitle-1">{{ img.title }}</h1>
                <p>
                  {{ img.copyright }}
                </p>
              </v-card-text>
            </v-flex>
          </div>
        </v-layout>
      </v-card>
    </v-container>
  </v-main>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      imgs: [],
    };
  },
  mounted() {
    axios
      .get("http://localhost:5000/api/7")
      .then((response) => {
        const arr = [];
        Object.keys(response.data).forEach((key) =>
          arr.push({
            id: key,
            copyright: response.data[key].copyright,
            url: response.data[key].url,
            title: response.data[key].title,
          })
        );
        this.imgs = arr;
      })
      .catch((err) => console.log(err));
  },
};
</script>