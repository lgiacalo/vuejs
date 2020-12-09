<template>
  <a :href="url">{{ name }}</a>
</template>

<script>
export default {
  name: "NavLink",
  props: {
    name: String,
    url: String,
  },
};
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>
