<template>
    <div class="wrapper">
        <img alt="Background Image" class="background" id="background" src="../assets/background.png">
        <div class="hero-wrapper">
            <p class="legend" id="legend">This image has been created by DallE (AI) especially for this website !</p>
            <div class="text">
                <p class="subtitle">The best Harry Potter wiki online !</p>
                <p class="title">Welcome to <b>Hogwarts</b></p>
                <p class="desc">Here you can check every character and spell of the Harry Potter Universe. You will be able
                    to see every character details and to add them to your favourites characters.   
                </p>
                <a href="#characters"><button class="check">Check this out !</button></a>
            </div>
        </div>
    </div>
    
  </template>
  
  <script>
  export default {
    name: 'Home',
    props: {
      msg: String
    }
  }

  /*window.onload=function(){
    let background = document.getElementById('background')
    background.addEventListener("mouseover", (event) => {
            document.getElementById('legend').style.transform = 'translate(0px)';
    });

    background.addEventListener("mouseout", (event) => {
            document.getElementById('legend').style.transform = 'translate(-205px)';
    });
  }*/
  
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>

  a {
    all: unset;
  }
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
        position: absolute;
        left: 0;
        z-index: 2;
    }

    .hero-wrapper {
        position: absolute;
        width: calc(100vw - 100vh) !important;
        height: 100vh;
        background-color: white;
        right: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    .text {
        width: 500px;
        height: 500px;
        display: flex;
        justify-content: center;
        align-items: flex-end;
        flex-direction: column;
    }

    .subtitle {
        font-size: 16px;
        text-align: right;
    }

    .title {
        font-size: 50px;
        align-self: center;
        width: 500px;
        text-align: right;
        margin: 15px;
    }

    .desc {
        font-size: 12px;
        width: 400px;
        text-align: right;
    }

    .check {
        all: unset;
        margin-top: 30px;
        width: 200px;
        height: 60px;
        text-align: center;
        border: 1px solid black;
        font-size: 12px;
        text-transform: uppercase;
        cursor: pointer;
        transition: all 0.3s ease-in-out;
    }

    .check:hover {
        background-color: black;
        color: white;
    } 
    
    .legend {
        position: absolute;
        top: 0;
        margin-top: 100px;
        width: 200px;
        font-size: 12px;
        align-self: flex-start;
        margin-left: 20px;
        transition: all 0.3s ease-in-out;
        transform: translateX(-205px);
    }
  </style>
  