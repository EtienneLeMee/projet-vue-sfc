<template>
  <div class="list" id="list">
    <characterList @characterName="GetCharacterName"/>
  </div>
  <div class="nav">
    <Nav/>
  </div>
  <div class="detail">
    <characterDetails character={{ characterName }}/>
  </div>
  <p>{{ character }}</p>
</template>

<script>
// @ is an alias to /src
import characterList from '@/components/characterList.vue'
import Nav from '@/components/Nav.vue'
import characterDetails from '@/components/characterDetails.vue'

export default {
  name: 'characterView',
  data() {
    return {
        characterName: '',
    };
  },
  components: {
    characterList,
    Nav,
    characterDetails
  },
  methods: {
    GetCharacterName: function(name) {
      this.characterName = name
      document.getElementById('list').style.display = 'none'
    }
  }
}
</script>

<style>
  nav {
    position: absolute;
    z-index: 3;
    right: 0;
  }

  .list {
    position: absolute;
    
  }

  .detail {
    position: absolute;
  }


</style>
