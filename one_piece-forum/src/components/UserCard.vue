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
  emits: ["change-name"],
};
</script>

<template>
  <div>
    <h1>User : {{ name }}</h1>
    <p>Favorite Food: {{ food }}</p>
    <button @click="$emit('change-name')">Change Name</button>
  </div>
</template>
