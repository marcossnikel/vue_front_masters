<script>
export default {
  data: () => ({
    count: 10,
    counterTitle: "Counter Standart",
    incrementAmount: 8,
  }),
  computed: {
    displayTitle() {
      if (this.count > 20) {
        return "Counter Standart - Very Long";
      } else {
        return "Counter Standart";
      }
    },
    optimizedIncrementAmount() {
      return this.displayTitle.length * this.incrementAmount;
    },
  },
  methods: {
    incrementCount(count, newAmount, event) {
      console.log(count);
      console.log(newAmount);
      console.log(event);
      this.count += this.optimizedIncrementAmount;
    },
  },
};
</script>

<template>
  <div>
    <h1>{{ displayTitle }}</h1>
    <p :data-increment-by="incrementAmount">Count : {{ count }}</p>
    <button @click="incrementCount(count, incrementAmount, $event)">
      Increment Count
    </button>
    <h1>{{ optimizedIncrementAmount }}</h1>
    <div>
      <label for="incrementAmount">Increment By:</label>
      <input type="number" v-model="incrementAmount" />
    </div>

    <hr />
  </div>
</template>
