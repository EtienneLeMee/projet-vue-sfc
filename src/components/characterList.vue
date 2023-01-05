<template>
  <div class="characterList">
    <h1>Characters</h1>
    <p>List of all characters in Harry Potter movies and books.</p>

    <div v-for="character in characters" id="list">
      <div class="card" v-on:click="getDetail(character.name)">
        <img v-if="character.image!==''" :src=character.image alt="Image" style="width: 30%" />
        <img v-if="character.image=='' && character.gender=='male'" src="../assets/wizzard.png" alt="Image" style="width: 30%" />
        <img v-if="character.image=='' && character.gender=='female'" src="../assets/wizzardfemale.png" alt="Image" style="width: 30%" />
        <div class="container">
          <h4>
            <b>{{ character.name }}</b>
          </h4>
          <img v-if="character.house == 'Gryffindor'" src="../assets/gryffindorLogo.png" style="width: 5%"/>
          <img v-else-if="character.house == 'Slytherin'" src="../assets/slytherinLogo.png" style="width: 5%"/>
          <img v-else-if="character.house == 'Hufflepuff'" src="../assets/hufflepuffLogo.png" style="width: 5%"/>
          <img v-else-if="character.house == 'Gryffindor'" src="../assets/ravenclawLogo.png" style="width: 5%"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
const apiURLCharacters = "https://hp-api.onrender.com/api/characters";
const apiURLHouses = "https://hp-api.onrender.com/api/house";
const config = {};

export default {
  name: "characterList",
  props: {
    msg: String,
  },
  data() {
    return {
      characters: null,
      selection: null,
    };
  },

  created: function () {
    this.fetchDataAsync();
  },

  methods: {
    fetchDataAsync: async function () {
      try {
        const responseChar = await axios.get(
          apiURLCharacters,
          config
        );
        this.characters = responseChar.data;
        console.log(responseChar.data)
      } catch (error) {
        console.log(error);
      }
    },
    getDetail: function (name) {
      this.$emit('characterName', name)
    },
    formattedMessage: function (message) {
      const newline = message.indexOf("\n");
      return newline > 0 ? message.slice(0, newline) : message;
    },
    formattedDate: function (date) {
      return date.replace(/T|Z/g, " ");
    },
  },
}
</script>



<style>
.card {
  /* Add shadows to create the "card" effect */
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
}

/* On mouse-over, add a deeper shadow */
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

/* Add some padding inside the card container */
.container {
  padding: 2px 16px;
}
</style>