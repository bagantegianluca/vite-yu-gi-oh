<script>
import axios from "axios";
import AppCard from "./AppCard.vue";
import AppFilter from "./AppFilter.vue";

export default {
  name: "AppMain",
  components: {
    AppCard,
    AppFilter,
  },
  data() {
    return {
      apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
      cards: [],
    };
  },
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
  <main>
    <div class="container">
      <AppFilter></AppFilter>
      <div class="row">
        <div class="col" v-for="card in cards">
          <AppCard :card="card"></AppCard>
        </div>
      </div>
    </div>
  </main>
</template>
<style scoped>
.container {
  width: 80%;
  max-width: 1680px;
  margin-inline: auto;
}

.row {
  padding: 2rem;
  background-color: var(--ygo-light);
  display: flex;
  flex-wrap: wrap;
}

.col {
  width: calc(100% / 5);
  padding: 1rem;
}
</style>
