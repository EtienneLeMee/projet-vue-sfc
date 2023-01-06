<template>
  <div class="list" id="list" v-bind:class="{ active: !isDetail }">
    <characterList @characterName="GetCharacterName"/>
  </div>
  <div class="nav">
    <Nav/>
  </div>
  <div class="detail" v-bind:class="{ active: isDetail }">
    <characterDetails @characterNameReset="CharacterNameReset" :character=characterName />
  </div>
  <p>{{ character }}</p>
</template>

<script>
// @ is an alias to /src

import Nav from '@/components/Nav.vue'
import characterList from '@/components/characterList.vue'
import characterDetails from '@/components/characterDetails.vue'

export default {
  name: 'characterView',
  data() {
    return {
        characterName: '',
        isDetail: false,
    };
  },
  components: {
    characterList,
    Nav,
    characterDetails
  },
  methods: {
    GetCharacterName: function(name) {
      this.isDetail = true
      this.characterName = name
      /*document.getElementById('list').style.display = 'none';
      document.getElementById('detail').style.display = 'block';*/
    },
    CharacterNameReset: function() {
      this.isDetail = false
      this.characterName = ""
      //document.getElementById('list').style.display = 'block';
    }
  }
}
</script>

<style>
  nav {
    position: absolute;
    z-index: 3;
    right: 0;
    margin-right: 40px;
  }

  .list {
    position: absolute;
    display: none;
    
  }

  .detail {
    position: absolute;
    display: none;
  }

  .active {
    display: block;
  }

</style>
