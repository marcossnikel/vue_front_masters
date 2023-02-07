<script>
export default {
  props: {
    name: {
      type: String,
      default: "Marko Niko",
    },
    food: {
      type: String,
      default: "Lunch",
    },
  },
};
</script>

<template>
  <div>
    <h1>User : {{ name }}</h1>
    <p>Favorite Food: {{ food }}</p>
  </div>
</template>
