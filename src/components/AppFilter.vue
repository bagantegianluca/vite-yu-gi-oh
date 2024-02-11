<script>
export default {
  name: "AppFilter",
  props: {
    archetypes: Array,
  },
  methods: {
    filteredCards(e) {
      /* console.log(e.target.value); */
      this.$emit("activeFilter", e.target.value);
    },
  },
};
</script>
<template>
  <select name="cards" id="cardsFilter" @change="filteredCards">
    <option value="All">All</option>
    <option v-for="archetype in archetypes" :value="archetype">
      {{ archetype }}
    </option>
  </select>
</template>
<style scoped>
select {
  margin-block: 1rem;
  margin-top: 5.5rem;
  padding: 0.5rem;
  border-radius: 5px;
}
</style>
