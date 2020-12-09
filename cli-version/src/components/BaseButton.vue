<template>
  <button v-on="$listeners">
    <slot name="text-button"></slot>
  </button>
</template>

<script>
export default {
  name: "BaseButton",
};
</script>
