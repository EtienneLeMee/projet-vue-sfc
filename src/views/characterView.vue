<template>
  <div class="home">
    <characterList/>
  </div>
  <div class="nav">
    <Nav/>
  </div>
</template>

<script>
// @ is an alias to /src
import characterList from '@/components/characterList.vue'
import Nav from '@/components/Nav.vue'

export default {
  name: 'characterView',
  components: {
    characterList,
    Nav
  }
}
</script>
