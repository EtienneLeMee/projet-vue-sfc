<template>
  <div class="Détails">
    <h1>{{ character }}</h1>
    <h3>{{ allCharacters }}</h3>
    <div v-for="characterS in allCharacters" v-if="character.name === 'character'">
      {{ characterS }}
    </div>
  </div>
</template>

<script>
const apiURL = "https://hp-api.onrender.com/api/characters";
const config = {};

export default {
  name: 'characterDetails',
  props: {
    character: String
  },

  data() {
    return {
      allCharacters: []
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
          console.log(response.data)
        })
        .catch(function(error) {
          console.log(error);
        });
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
