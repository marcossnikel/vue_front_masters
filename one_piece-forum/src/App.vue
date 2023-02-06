<script>
export default {
  data() {
    //data in function to maintain the reactivity and just pull out the last instance of that object
    return {
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
        show: false,
      },
      count: 10,
      // counterTitle : 'Counter Standart',
      incrementAmount: 8,
      message: "Aobaasass",
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
    };
  },
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
  methods: {
    incrementCount(count, newAmount, event) {
      console.log(count);
      console.log(newAmount);
      console.log(event);
      this.count += this.optimizedIncrementAmount;
      console.log(this.persons.chars);
    },
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
  watch: {
    // count(newValue){
    //   // if(newValue > 20) this.counterTitle += " GRANDE";
    // }
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
    </pre>
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

    <br /><br /><br /><br /><br /><br /><br /><br /><br />
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
    <hr />
  </div>
</template>
