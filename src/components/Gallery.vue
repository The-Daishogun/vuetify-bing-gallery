<template>
  <v-layout row class="justify-space-around">
    <v-flex
      xs12
      md3
      v-for="(value, key) in imgs"
      :key="key"
      class="ma-3"
      :id="`flex-${key}`"
    >
      <v-card class="pa-3">
        <v-layout row>
          <v-flex xs12 md5>
            <v-img
              :src="`${value.url}`"
              class="mx-3"
              :id="`img-${key}`"
            ></v-img>
          </v-flex>
          <v-flex xs12 md7>
            <h1 class="subtitle-1 mx-3">{{ value.title }}</h1>
            <p class="caption text-truncate mx-3" :id="`text-${key}`">
              {{ value.copyright }}
            </p>
            <v-btn small text :id="`${key}`" @click="showText">Show Text</v-btn>
            <v-btn small text :id="`${key}`" @click="enlargeImage"
              >Enlarge Image</v-btn
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
      var elem = event.target.parentElement;
      document
        .getElementById(`text-${elem.id}`)
        .classList.toggle("text-truncate");
    },
    enlargeImage(event) {
      var id = event.target.parentElement.id;
      var selected = document.getElementsByClassName("selected")[0];
      var elem = document.getElementById(`flex-${id}`);

      if (elem.classList.contains("selected")) {
        return;
      } else {
        elem.classList.add("selected");
        selected.classList.remove("selected");
        var smallImageURL = document.getElementById(`img-${id}`).childNodes[1]
          .style.backgroundImage;
        this.$emit("img-url", smallImageURL.slice(5, -2));
      }
    },
  },
  created() {
    axios
      .get("http://localhost:5000/api/7")
      .then((response) => {
        this.imgs = response.data;
      })
      .then(() => {
        document.getElementById("flex-0").classList.add("selected");
        var latestURL = this.imgs["0"].url;
        this.$emit("img-url", latestURL);
      })
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.selected {
  border: 5px solid pink;
  border-radius: 5px;
}
</style>