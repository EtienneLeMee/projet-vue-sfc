<template>
    <button v-on:click="resetName()" id="back">Back</button>
    <h1>{{ character }}</h1>
    <template v-for="characterSearch in allCharacters">
      <template v-if="characterSearch.name === character">
        <img class="character image" :src="characterSearch.image" alt="nothing">
        <h2>General</h2>
        <p>Name : </p><input type="text" v-model="characterSearch.name" disabled>
        <p>Species : </p><input type="text" v-model="characterSearch.species" disabled>
        <p>Gender : </p><input type="text" v-model="characterSearch.gender" disabled>
        <p>Date Of Birth : </p><input type="text" v-model="characterSearch.dateOfBirth" disabled>

        <p>Status : </p>
        <div class="alive" v-if="characterSearch.alive">
          <input type="text" value="Alive" disabled>
        </div>
        <div class="alive" v-else>
          <input type="text" value="Dead" disabled>
        </div>

        <h2>Appearance</h2>
        <p>Eye color : </p><input type="text" v-model="characterSearch.eyeColour" disabled>
        <p>Hair color : </p><input type="text" v-model="characterSearch.hairColour" disabled>
        <h2>At Hogwart</h2>
        <p>House : </p><input type="text" v-model="characterSearch.house" disabled>
        <p>Hogwart relation :</p>
        <div class="hogwartRelation" v-if="characterSearch.hogwartsStudent">
          <input type="text" value="Student at Hogwart" disabled>
        </div>
        <div class="hogwartRelation" v-else-if="characterSearch.hogwartsStudent">
          <input type="text" value="Teacher at hogwart" disabled>
        </div>
        <div class="hogwartRelation" v-else-if="characterSearch.hogwartsStudent">
          <input type="text" value="No relation with hogwart" disabled>
        </div>
        <br>
        <h2>About his magic</h2>
        <p>Wand composition : </p>
        <p>Wood :</p><input type="text" v-model="characterSearch.wand.wood" disabled>
        <p>Core :</p><input type="text" v-model="characterSearch.wand.core" disabled>
        <p>Length :</p><input type="text" v-model="characterSearch.wand.length" disabled>
        <p>Patronus : </p><input type="text" v-model="characterSearch.patronus" disabled>
      </template>
    </template>
</template>

<script>
const apiURL = "https://hp-api.onrender.com/api/characters";
const config = {};
import axios from 'axios'



export default {
  name: 'characterDetails',
  props: {
    character: String
  },

  data() {
    return {
      allCharacters: [],
  };
},

created: function() {
    this.fetchCharacter();
},

methods: {
  fetchCharacter: function() {
    const self = this;
    axios
        .get(apiURL, config)
        .then(function(response) {
            self.allCharacters = response.data;
        })
        .catch(function(error) {
            console.log(error);
        });
  },
  resetName: function () {
      this.$emit('characterNameReset')
    },
},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

</style>
