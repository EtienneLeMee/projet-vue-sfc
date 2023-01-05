<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <spellsList msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import spellsList from '@/components/SpellList.vue'

export default {
  name: 'spellView',
  components: {
    spellsList
  }
}
</script>
