<template class="wrapper">
  <div class="cards">
    <div v-for="user in users.data" :key="user.id">
      <UsersCard
        :username="user.name"
        :email="user.email"
        :phone="user.phone"
      />
    </div>
  </div>
</template>

<script>
import UsersCard from "./UsersCard.vue";
import axios from "axios";
export default {
  data: () => ({
    users: [],
  }),

  methods: {
    async fetchUsers() {
      this.users = await axios
        .get("https://jsonplaceholder.typicode.com/users")
        .then((res) => {
          this.users = res;
          console.log(res.data);
        });
    },
  },
  created() {
    this.fetchUsers();
  },
  components: {
    UsersCard,
  },
};
</script>

<style>
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: red;
  width: 100%;
  height: 100%;
}

.cards {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 30px;
}
</style>
