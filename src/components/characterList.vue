<template>
  <div class="characterList">
    <h1>{{ msg }}</h1>
    <p>List of all characters in Harry Potter movies and books.</p>

    <div id="list">
      <div class="card">
        <img src={{image}} alt="Image" style="width: 100%" />
        <div class="container">
          <h4>
            <b>{{ name }}</b>
          </h4>
          <p>More</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from axios;
const apiURLCharacters = "https://hp-api.onrender.com/api/characters";
export default {
  name: "characterList",
  props: {
    msg: String,
  },
  data() {
    return {
      characters: null,
    };
  },

  created: function () {
    this.startFetchDataAsync();
  },

  watch: {
    currentType: "fetchDataAsync",
  },

  methods: {
    fetchDataAsync: async function () {
      try {
        const responseType = await axios.get(
          apiURLType + this.currentType,
          config
        );
        console.log(responseType.data);
        this.lieuxParType = responseType.data.facet_groups[1].facets;
        this.recordsParType = responseType.data.records;
        // console.log(self.commits[0].html_url);
      } catch (error) {
        console.log(error);
      }
    },
    startFetchDataAsync: async function () {
      try {
        const responseDechets = await axios.get(apiURLCharacters, config);
        console.log(responseType.data);
        this.dechets = responseDechets.data.facet_groups[0].facets;
        this.lieuxParType = responseType.data.facet_groups[1].facets;
        this.recordsParType = responseType.data.records;
        // console.log(self.commits[0].html_url);
      } catch (error) {
        console.log(error);
      }
    },
    makeActive: function (name) {
      this.currentType = name;
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
