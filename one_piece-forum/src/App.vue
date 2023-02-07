<script>
import Counter from "./components/BaseCounter.vue";
import LearningListCounter from "./components/LearningListCounter.vue";
import OnePieceComponent from "./components/OnePieceComponent.vue";
import StatisticsModule from "./components/StatisticsModule.vue";
import UserCard from "./components/UserCard.vue";

export default {
  components: {
    Counter,
    OnePieceComponent,
    LearningListCounter,
    StatisticsModule,
    UserCard,
  },

  data: () => ({
    persons: {
      chars: [
        {
          name: "Luffy",
          age: 18,
          powers: ["Gum", "Haki", "Haoshoku", "Lightning"],
        },
        {
          name: "Zoro",
          age: 22,
          powers: ["Sword", "Haki", "Strengh", "Haoshoku"],
        },
        {
          name: "Nami",
          age: 22,
          powers: ["Lightning", "Zeus"],
        },
        {
          name: "Sanji",
          age: 28,
          powers: ["Kick", "Haki", "DNA"],
        },
        {
          name: "Robin",
          age: 31,
          powers: ["Knowledge", "Akuma no Mi", "Vision"],
        },
        {
          name: "Usopp",
          age: 23,
          powers: ["Vision", "Toxic Plants"],
        },
        {
          name: "Katakuri",
          age: 54,
          powers: [
            "Vision Haki",
            "Akuma no Mi",
            "Knowledge",
            "Vision",
            "Haoshoku",
          ],
        },
      ],
    },
    userData: {
      name: "marko",
      preferredFramework: "vue",
      favoriteFood: "meat",
      favoriteNumber: [7, 14, 21],
    },
  }),
  computed: {},
};
</script>

<template>
  <div>
    <user-card :name="userData.name" :food="userData.favoriteFood" />
    <counter />
    <one-piece-component :charsProp="persons.chars" />
    <learning-list-counter />
    <statistics-module :characters="persons.chars" />
  </div>
</template>
