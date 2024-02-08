<script>
import axios from "axios";
import AppHeader from "../src/components/AppHeader.vue";

export default {
  name: "App",
  data() {
    return {
      apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
      cards: [],
    };
  },
  components: {
    AppHeader,
  },
  methods: {},
  mounted() {
    axios
      .get(this.apiUrl)
      .then((response) => {
        this.cards = response.data.data;
      })
      .catch((error) => {
        console.log(error.message);
      });
  },
};
</script>

<template>
  <AppHeader></AppHeader>
  <div v-for="card in cards">
    <img :src="card.card_images[0].image_url_small" alt="" />
    <p>{{ card.name }}</p>
    <p>{{ card.archetype }}</p>
  </div>
</template>

<style scoped></style>
