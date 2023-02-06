<script>
export default {
  data: () => ({
    newCharacter: {
      name: "",
      age: "",
    },
    chars: ["Luffy", "Zoro", "Nami"],
    favorites: [],
    favoritesList: [],
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
  }),
  methods: {
    addCharToFavorite(character) {
      this.favorites.push(character);
      console.log("favorites list", this.favorites);
    },
    removeFavorite(char) {
      console.log(char.name);
      this.favorites.shift();
    },
    addNewCharacter() {
      console.log(this.newCharacter.name);
      this.persons.chars.push({
        name: this.newCharacter.name,
        age: this.newCharacter.age,
      });
      console.log(this.persons);
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
      this.persons.chars.forEach((character) => {
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
    <p v-if="persons.show == true">No persons bro</p>

    <p v-else v-for="(person, index) in persons.chars" :key="`item${index}`">
      Name : {{ person.name }} <br />
      Age : {{ person.age }}
      <button @click="addCharToFavorite(person)">Favorite Char</button>
    </p>
    <div>
      <h3>Favorite Chacracters</h3>
      <ul>
        <li v-for="(char, index) in favorites" :key="`char${index}`">
          {{ char.name }}
          <button @click="removeFavorite(char)">Remove Favorite</button>
        </li>
      </ul>
    </div>

    <p>
      <span v-for="(char, index) in persons.chars" :key="`char${index}`">
        {{ char.name }}{{ index == persons.chars.length - 1 ? "" : "," }}
      </span>
    </p>
  </div>
</template>
