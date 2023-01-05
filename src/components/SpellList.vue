<template>
  <div class="SpellList">
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
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
