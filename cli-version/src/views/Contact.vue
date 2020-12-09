<template>
  <div>
    <h2>Contactez nous</h2>
    <p>Adresse : {{ addresse }}</p>
    <p>Téléphone : {{ phone }}</p>
    <p>Email : {{ email }}</p>
    <p>Horaires :</p>
    <ul>
      <li>L-V: 06:00 à 16:00</li>
      <li>Samedi: 07:00 à 14:00</li>
      <li>Dimanche: 07:00 à 12:00</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function() {
    return {
      addresse: "18 avenue du Beurre, Paris, France",
      phone: "01 88 88 88 88",
      email: "hello@cafewithavue.bakery",
    };
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
