<script>
export default {
  data: () => ({
    message: "Aobaasasss",
    listofNumbers: [
      {
        name: 1,
        id: "d5eaaaf6-866b-413e-ad88-59c694ff6307",
        list: [1, 2, 3],
      },
      {
        name: 2,
        id: "e4997ae7-3503-4b0b-bb98-1c76bf4eb34b",
        list: [1, 2, 3],
      },
      {
        name: 3,
        id: "7f8e9b17-fd5a-4d72-ab9a-2646bde1d5f0",
        list: [1, 2, 3],
      },
      {
        name: 4,
        id: "6b8a5118-4e67-45d2-8e24-85201098fe15",
        list: [1, 2, 3],
      },
      {
        name: 5,
        id: "480cae9c-3bbf-4344-b4c9-278acb34b983",
        list: [1, 2, 3],
      },
    ],
  }),
};
</script>

<template>
  <div>
    <p v-if="message.length % 2 === 0">Even : {{ message.toUpperCase() }}</p>
    <p v-else>Odd : {{ message }}</p>
    <ul v-for="(item, index) in listofNumbers" :key="`item${index}`">
      <li>{{ item.id }}</li>
      <ul>
        <li v-for="(number, idx) in item.list" :key="`number${idx}`">
          {{ number }}
        </li>
      </ul>
    </ul>
  </div>
</template>
