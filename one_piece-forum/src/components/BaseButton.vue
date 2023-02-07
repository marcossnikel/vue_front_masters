<script>
export default {
  props: {
    left: Boolean,
    default: false,
  },
};
</script>

<template>
  <button>
    <slot v-if="left"> Submit </slot>
    <slot v-else>Cancel</slot>
  </button>
</template>
