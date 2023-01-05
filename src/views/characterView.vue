<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <characterList msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import characterList from '@/components/characterList.vue'

export default {
  name: 'characterView',
  components: {
    characterList
  }
}
</script>
