<template>
    <div class="wrapper">
      <div class="container">
        <div v-for="spell in spells" id="list" class="list">
          <p class="name">{{spell.name}}</p><br>
          <p class="desc">{{ spell.description }}</p>
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
* {
  all: unset;
}
  .wrapper {
    width: 100vw;
    position: absolute;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }

  .container {
    margin-top: 100px;
    width: 90vw;
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    column-gap: 10px;
    row-gap: 10px;
  }

  .list {
    width: 200px;
    height: 130px;
    background-color: rgb(230, 230, 230);
    position: relative;
  }

  .card {
    
  }

  .desc {
    font-size: 10px;
  }
</style>
