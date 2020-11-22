<template>
  <v-layout row class="justify-space-around">
    <v-flex xs12 md3 v-for="img in imgs" :key="img.id" class="ma-3">
      <v-card class="pa-3">
        <v-layout row>
          <v-flex xs12 md5>
            <v-img :src="`${img.url}`" class="mx-3"></v-img>
          </v-flex>
          <v-flex xs12 md7>
            <h1 class="subtitle-1 mx-3">{{ img.title }}</h1>
            <p class="caption text-truncate mx-3" :id="`text-${img.id}`">
              {{ img.copyright }}
            </p>
            <v-btn small text :id="`${img.id}`" @click="showText"
              >Show Text</v-btn
            >
          </v-flex>
        </v-layout>
      </v-card>
    </v-flex>
  </v-layout>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      imgs: [],
    };
  },
  methods: {
    showText(event) {
      var id = event.target.parentElement.id;
      document.getElementById(`text-${id}`).classList.toggle("text-truncate");
    },
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