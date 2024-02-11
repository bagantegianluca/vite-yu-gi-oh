<script>
import axios from "axios";
import AppCard from "./AppCard.vue";
import AppFilter from "./AppFilter.vue";
import AppCardsCounter from "./AppCardsCounter.vue";

export default {
  name: "AppMain",
  components: {
    AppCard,
    AppFilter,
    AppCardsCounter,
  },
  data() {
    return {
      apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
      cards: [],
      filteredCards: [],
      filteredCardsNo: 0,
      archetypes: [],
    };
  },
  methods: {
    getActiveFilter(value) {
      /* console.log(value); */
      this.filteredCards = this.cards.filter((card) =>
        value === "All" ||
        card.archetype === value ||
        (!card.archetype && value === "Undefined")
          ? true
          : false
      );
      this.filteredCardsNo = this.filteredCards.length;
      /* console.log(filteredCards); */
    },
  },
  mounted() {
    axios
      .get(this.apiUrl)
      .then((response) => {
        this.cards = response.data.data;
        this.cards.forEach((card) =>
          !this.archetypes.includes(
            card.archetype ? card.archetype : "Undefined"
          )
            ? this.archetypes.push(
                card.archetype ? card.archetype : "Undefined"
              )
            : ""
        );
        this.filteredCards = [...this.cards];
        this.filteredCardsNo = this.filteredCards.length;
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
      <AppFilter
        :archetypes="archetypes.sort()"
        @activeFilter="getActiveFilter"
      ></AppFilter>
      <AppCardsCounter :filteredCardsNo="filteredCardsNo"></AppCardsCounter>
      <div class="row">
        <div class="col" v-for="card in filteredCards">
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

@media screen and (max-width: 1400px) {
  .col {
    width: 25%;
  }
}

@media screen and (max-width: 1100px) {
  .container {
    width: 100%;
  }
  .col {
    width: calc(100% / 3);
  }
}

@media screen and (max-width: 800px) {
  .col {
    width: 50%;
  }
}

@media screen and (max-width: 600px) {
  .col {
    width: 100%;
  }
}
</style>
