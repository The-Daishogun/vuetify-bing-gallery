<template>
  <v-layout row class="justify-center my-5">
    <v-flex md9>
      <v-card class="justify-space-around" shaped height="20%">
        <v-img :src="`${url}`"></v-img>
      </v-card>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  props: ["url"],
};
</script>