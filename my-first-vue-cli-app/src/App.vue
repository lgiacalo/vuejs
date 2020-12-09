<template>
  <div id="app">
    <nav>
      <NavLink name="Accueil" url="/accueil" />
      <NavLink name="A propos" url="/about" />
      <NavLink
        v-bind="{
          name: 'Contact',
          url: '/contact',
        }"
      />
    </nav>
    <p>Bienvenu sur notre page d'<a href="/">Accueil</a></p>
  </div>
</template>

<script>
import NavLink from "./components/NavLink.vue";

export default {
  name: "App",
  components: {
    NavLink,
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
