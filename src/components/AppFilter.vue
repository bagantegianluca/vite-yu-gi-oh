<script>
export default {
  name: "AppFilter",
};
</script>
<template>
  <select name="cards" id="cardsFilter">
    <option value="">--Please choose an option--</option>
    <option value="Alien">Dog</option>
    <option value="Infernoble Arms">Cat</option>
    <option value="Noble Knight">Hamster</option>
    <option value="Melodious">Parrot</option>
    <option value="Archfiend">Spider</option>
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
