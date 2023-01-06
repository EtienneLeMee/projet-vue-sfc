<template>
  <p class="title">Characters</p>
  <p class="desc">List of all characters in Harry Potter movies and books.</p>
  <div class="wrapper">
    <div class="grid">
      <div v-for="character in characters" id="list" class="card" v-on:click="getDetail(character.name)">
        <img v-if="character.image!==''" :src=character.image alt="Image" style="width: 30%" class="avatar"/>
        <img v-if="character.image=='' && character.gender=='male'" src="../assets/wizzard.png" alt="Image" style="width: 30%" class="avatar"/>
        <img v-if="character.image=='' && character.gender=='female'" src="../assets/wizzardfemale.png" alt="Image" style="width: 30%" class="avatar"/>
        <div class="container">
          <h4>
            <b>{{ character.name }}</b>
          </h4>
          <img v-if="character.house == 'Gryffindor'" src="../assets/gryffindorLogo.png" style="width: 30px; margin-top: 20px;"/>
          <img v-else-if="character.house == 'Slytherin'" src="../assets/slytherinLogo.png" style="width: 30px; margin-top: 20px;"/>
          <img v-else-if="character.house == 'Hufflepuff'" src="../assets/hufflepuffLogo.png" style="width: 30px; margin-top: 20px;"/>
          <img v-else-if="character.house == 'Ravenclaw'" src="../assets/ravenclawLogo.png" style="width: 30px; margin-top: 20px;"/>
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



<style scoped>



.wrapper {
  width: 100vw;
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 40px;
  max-width: 100%;
}

.grid {
  width: 85vw;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  column-gap: 10px;
  row-gap: 20px;
}


.card {
  transition: 0.3s;
  width: 280px;
  height: 150px;
  background-color: rgb(246, 246, 246);
  padding: 10px;
  cursor: pointer;
  border-radius: 20px;
  color: black;
  font-family: 'Lato', sans-serif;
  transition: all 0.3s ease-in-out;
}


.card:hover {
  background-color: rgb(221, 221, 221);
}


.container {
  padding: 2px 16px;
}

.avatar {
  max-width: 100px;
  float: right;
  border-radius: 10px;
}

.title {
  margin-top: 40px;
  margin-left: 100px;
  font-family: 'Lato', sans-serif;
  font-size: 20px;
  font-weight: 600;
  color: black;
}

.desc {
  margin-top: 5px;
  margin-left: 100px;
  font-family: 'Lato', sans-serif;
  font-size: 15px;
  font-weight: 400;
  color: #4C308B;
}

</style>