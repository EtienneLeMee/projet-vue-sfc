<template>
  <p class="title">Spells</p><br>
  <p class="desc2">List of all spells in Harry Potter movies and books.</p>
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
    width: 98vw;
    height: auto;
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
    grid-template-columns: repeat(5, 1fr);
    column-gap: 10px;
    row-gap: 10px;
    margin-bottom: 50px;
  }

  .list {
    width: 230px;
    height: 160px;
    background-color: rgb(246, 246, 246);
    position: relative;
    padding: 10px;
    border-radius: 20px;
  }

  .name {

  }

  .desc {
    font-size: 10px;
    color: grey;
  }

  .title {
    position: absolute;
  margin-top: 40px;
  margin-left: 100px;
  font-family: 'Lato', sans-serif;
  font-size: 20px;
  font-weight: 600;
  color: black;
}

.desc2 {
  position: absolute;
  width: 400px;
  margin-top: 50px;
  margin-left: 100px;
  font-family: 'Lato', sans-serif;
  font-size: 15px;
  font-weight: 400;
  color: #4C308B;
}

  @media (max-width: 1350px) {
    .container {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  @media (max-width: 1100px) {
    .container {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  @media (max-width: 900px) {
    .container {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>
