<!-- eslint-disable vue/no-mutating-props -->
<script>
import CharacterCard from "./CharacterCard.vue";
export default {
  components: { CharacterCard },
  props: ["charsProp"],
  data: () => ({
    newCharacter: {
      name: "",
      age: "",
    },
    chars: ["Luffy", "Zoro", "Nami"],
    favoritesList: [],
  }),
  methods: {
    removeFavorite(char) {
      console.log(char.name);
      this.favorites.shift();
    },
    addNewCharacter() {
      console.log(this.newCharacter.name);
      this.charsProp.push({
        name: this.newCharacter.name,
        age: this.newCharacter.age,
      });
      console.log(this.persons);
    },
    addFavoriteCharacter(payload) {
      console.log(this.favoritesList);
      this.favoritesList.push(payload);
    },
  },
  computed: {},
};
</script>

<template>
  <div>
    <h2>Characters</h2>
    <p>{{ chars }}</p>
    <pre>
          {{ newCharacter }}
      </pre
    >
    <label for="charName">Character Name</label>
    <input
      type="text"
      id="charName"
      v-model="newCharacter.name"
      @keyup.enter="addNewCharacter"
    />
    <label for="">Age</label>
    <input
      type="text"
      id="charName"
      v-model="newCharacter.age"
      @keyup.enter="addNewCharacter"
    />
    <!-- <button @click="addNewChar(chars,newCharacter,$event)">Add New Char </button> -->

    <p v-for="(charsProp, index) in charsProp" :key="`item${index}`">
      <character-card :character="charsProp" @favorite="addFavoriteCharacter" />
    </p>
    <div>
      <h3>Favorite Chacracters</h3>
      <ul>
        <li
          v-for="(char, index) in favoritesList"
          :key="`char${index}`"
          style="list-style-type: none"
        >
          <p>
            Name : {{ char.name }} <br />
            Age : {{ char.age }}
          </p>
        </li>
      </ul>
    </div>

    <p>
      <span v-for="(char, index) in charsProp" :key="`char${index}`">
        {{ char.name }}{{ index == charsProp.length - 1 ? "" : "," }}
      </span>
    </p>
  </div>
</template>
