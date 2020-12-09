<template>
  <button v-on="$listeners">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "BaseButton",
  props: {
    text: String,
  },
};
</script>
