<template>
    <div class="wrapper">
        <img alt="Background Image" class="background" src="../assets/background.png">
        <div class="hero-wrapper"></div>
    </div>
    
  </template>
  
  <script>
  export default {
    name: 'Header',
    props: {
      msg: String
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
    .wrapper {
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-content: center;
    }
    
    .background {
        height: 100vh;
        justify-self: flex-start;
    }

    .hero-wrapper {
        width: 500px;
        height: 100vh;
        background-color: blue;
    }
  </style>
  