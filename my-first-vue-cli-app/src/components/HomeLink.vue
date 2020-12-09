<template>
  <a :href="url">{{ name }}</a>
</template>

<script>
export default {
  name: "HomeLink",
  data: function() {
    return {
      name: "Accueil",
      url: "./accueil",
    };
  },
};
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>
