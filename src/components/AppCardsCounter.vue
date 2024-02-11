<script>
export default {
  name: "AppCardsCounter",
  props: {
    filteredCardsNo: Number,
  },
};
</script>
<template>
  <div class="cardsCounter">Found {{ filteredCardsNo }} cards</div>
</template>
<style scoped>
.cardsCounter {
  background: var(--ygo-dark);
  color: var(--ygo-light);
  font-weight: bold;
  padding: 1rem;
}
</style>
