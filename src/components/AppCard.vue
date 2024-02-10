<script>
export default {
  name: "AppCard",
  props: {
    card: Object,
  },
  /*   computed: {
    showArchetype(archetype) {
      return archetype ? archetype : "Undefined";
    },
  }, */
};
</script>
<template>
  <div class="card">
    <img :src="card.card_images[0].image_url_small" alt="" />
    <div class="card-info">
      <div class="card-name">{{ card.name }}</div>
      <div class="card-archetype">
        {{
          /* showArchetype(card.archetype) */ card.archetype
            ? card.archetype
            : "Undefined"
        }}
      </div>
    </div>
  </div>
</template>
<style scoped>
.card {
  width: 100%;
  background: var(--ygo-primary);
  height: 100%;
  img {
    width: 100%;
  }
}

.card-info {
  padding: 1rem;
}

.card-name {
  color: var(--ygo-light);
  text-transform: uppercase;
  font-weight: bold;
  margin-bottom: 1rem;
}

.card-name,
.card-archetype {
  text-align: center;
  font-weight: bold;
}
</style>
