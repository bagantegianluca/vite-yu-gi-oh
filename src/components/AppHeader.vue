<script>
export default {
  name: "AppHeader",
  data() {
    return {
      imgUrl:
        "https://www.yugioh-card.com/eu/wp-content/themes/yugioh/images/logo/Yugioh-EN-DE.svg",
    };
  },
};
</script>
<template>
  <header>
    <img :src="imgUrl" alt="logo" />
    <h1>Yu-Gi-Oh Api</h1>
  </header>
</template>
<style scoped>
header {
  position: fixed;
  width: 100%;
  background: var(--ygo-light);
  padding: 1rem;
  display: flex;

  img {
    max-height: 40px;
    margin-right: 1rem;
  }
}
</style>
