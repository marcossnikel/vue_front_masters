<!-- BASEURL - https://pokeapi.co/api/v2/pokemon?limit=151 -->

<script>
export default {
  data: () => ({
    pokedex: [1, 2, 3, 4],
  }),
  methods: {
    async fetchPokemon() {
      this.pokedex = await fetch(
        "https://pokeapi.co/api/v2/pokemon?limit=151"
      ).then((res) => res.json());
    },
  },
  created() {
    this.fetchPokemon();
  },
};
</script>

<template>
  <div>
    <h1>new app</h1>
    <pre>{{ pokedex }}</pre>
    <button @click="fetchPokemon">Fetch Pokemon</button>
  </div>
</template>

<style></style>
