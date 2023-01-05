<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <SpellList spellmsg
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import SpellList from "@/components/SpellList";

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    SpellList,
  }
}
</script>
