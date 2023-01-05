<template>
    <nav>
        <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#characters">Characters</a></li>
            <li><a href="#spells">Spells</a></li>
        </ul>
    </nav>
  </template>
  
  <script>
  export default {
    name: 'Nav',
    props: {
      msg: String
    }
  }


  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>

ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
  }

  li {
    float: left;
  }

  li a {
    display: block;
    color: #666;
    text-align: center;
    padding: 14px 25px;
    text-decoration: none;
    transition: all 0.3s ease-in-out;
  }

  li a:hover:not(.active) {
    text-decoration: underline;
  }

  li a.active {
    color: black;
    border-bottom: 2px solid black;
  }
  </style>
  