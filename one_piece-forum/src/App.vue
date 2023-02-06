<script>
import Counter from "./components/BaseCounter.vue";
import LearningListCounter from "./components/LearningListCounter.vue";
import OnePieceComponent from "./components/OnePieceComponent.vue";

export default {
  components: {
    Counter,
    OnePieceComponent,
    LearningListCounter,
  },

  data: () => ({}),
  computed: {},
};
</script>

<template>
  <div>
    <counter />
    <one-piece-component />
    <learning-list-counter />
  </div>
</template>
