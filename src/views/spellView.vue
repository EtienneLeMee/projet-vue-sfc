<template>
  <div class="home">
    <spellsList/>
  </div>
  <div class="nav">
    <Nav/>
  </div>
</template>

<script>
// @ is an alias to /src
import spellsList from '@/components/SpellList.vue'
import Nav from '@/components/Nav.vue'

export default {
  name: 'spellView',
  components: {
    spellsList,
    Nav
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
</style>
