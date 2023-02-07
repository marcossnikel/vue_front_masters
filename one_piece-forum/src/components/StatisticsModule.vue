<script>
export default {
  props: {
    characters: {
      type: Array,
      required: true,
    },
  },
  computed: {
    powerStatistics() {
      const possiblePowers = ["Haoshoku", "Haki", "Vision", "Lightning"];

      const statistics = {
        Haoshoku: 0,
        Haki: 0,
        Vision: 0,
        Lightning: 0,
      };
      this.characters.forEach((character) => {
        if (!character) return null;
        possiblePowers.forEach((powers) => {
          if (!character.powers) return null;
          if (character.powers.indexOf(powers) > -1) {
            statistics[powers] += 1;
          }
        });
      });

      return statistics;
    },
  },
};
</script>

<template>
  <div>
    <h2>Statistics</h2>
    <ul>
      <li
        v-for="(stats, power) in powerStatistics"
        :key="`stats${stats},${power}`"
      >
        {{ power }}: {{ stats }}
      </li>
    </ul>
  </div>
</template>
