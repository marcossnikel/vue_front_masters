<script>
export default {
  data: () => ({}),
  props: {
    username: {
      type: String,
      required: false,
    },
    email: {
      type: String,
      required: false,
    },
    phone: {
      type: String,
      required: false,
    },
  },
};
</script>

<template>
  <div class="card_container">
    <h3 class="card_container-name">Name : {{ username }}</h3>
    <br />
    <div class="card_container-info">
      <span class="text">Email: {{ email }}</span>
      <span class="text">Phone : {{ phone }} </span>
    </div>
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@0,400;1,100;1,200&display=swap");

.card_container-info {
  display: flex;
  justify-content: space-around;
  gap: 5px;
  flex-wrap: wrap;
}
.card_container-name {
  font-family: "Roboto Mono";
  font-weight: 400;
}
.text {
  font-family: "Roboto Mono";
  font-weight: 100;
}
.card_container {
  box-sizing: border-box;
  padding: 2rem;
  width: 300px;
  height: 300px;
  border-radius: 1rem;
  background-color: purple;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  overflow: hidden;
}
</style>
