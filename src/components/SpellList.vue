<template>
  <div class="spellList">
      <h1>Characters</h1>
      <p>List of all spells in Harry Potter movies and books.</p>

      <div v-for="spell in spells" id="list">
        <div class="card">
          <b style="color: chocolate">{{spell.name}}</b>
          <div class="container">
            <h4>
              <b>{{ spell.description }}</b>
            </h4>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';
const apiURLSpells = "https://hp-api.onrender.com/api/spells";
const config = {};

export default {
  name: "spellsList",
  props: {
    msg: String,
  },
  data() {
    return {
      spells: null,
    };
  },

  created: function () {
    this.fetchDataAsync();
  },

  methods: {
    fetchDataAsync: async function () {
      try {
        const responseChar = await axios.get(
            apiURLSpells,
            config
        );
        this.spells = responseChar.data;
        console.log(responseChar.data)
      } catch (error) {
        console.log(error);
      }
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
