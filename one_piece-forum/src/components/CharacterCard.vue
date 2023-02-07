<script>
export default {
  props: {
    character: {
      type: Object,
      required: true,
    },
  },
  emits: ["favorite"],
  methods: {
    favoriteCharacter() {
      this.$emit("favorite", this.character);
    },
  },
};
</script>

<template>
  <div>
    <p>
      Name : {{ character.name }} <br />
      Age : {{ character.age }}
    </p>
    <button @click="favoriteCharacter">Favorite Char</button>
  </div>
</template>
