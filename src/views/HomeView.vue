<template>
  <main>
    <div class="advice">
      <h1>ADVICE {{this.id}}</h1>
      <p>"{{this.info}}"</p>
      <img src="/src/assets/images/pattern-divider-desktop.svg" alt="" id="divider">
      <button @click="getAdvice"><img src="/src/assets/images/icon-dice.svg" alt="" id="img"></button>
    </div>
  </main>
</template>

<script>
  import axios from 'axios'
   export default{
    name: 'Advice gen',
    data() {
      return {
        info: '',
        id: 0    
      };
    },

    mounted() {
      axios.get('https://api.adviceslip.com/advice')
       .then(response=> {
       const data = response.data
       this.id = data.slip.id
       this.info = data.slip.advice
    })
    
    },

    methods: {
      getAdvice () {
        axios.get('https://api.adviceslip.com/advice')
       .then(response=> {
       const data = response.data
       this.id = data.slip.id
       this.info = data.slip.advice
       console.log(data)
       console.log(this.id)
       console.log(this.info)
    })
        let deg = 0
        deg+=45
        console.log(deg)
       document.getElementById('img').style.transform = 'rotate("deg"deg)'
       document.getElementById('img').style.transition = '.5s ease-in '
    
      }
      
    }

    
  }
</script>


<style >
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@500;700&display=swap');
  main {
    width: 100%;
    height: 100vh;
    color: white;
    background-color: hsl(218, 23%, 16%);
    font-family: 'Manrope', sans-serif;
    
  }

  .advice {
    position: absolute;
    background-color: hsl(217, 19%, 24%);
    /* width: min(500px, 50%); */
    width: 50%;
    height: 350px;
    top: 30vh;
    left: 35vw;
    border-radius: 15px;
    text-align: center;
    padding: 30px 30px 30px 30px;
    justify-content: center;
    
  }

  .advice p {
    justify-content: center;
    font-size: 28px;
    color: hsl(193, 38%, 86%);
    height: 100px;
    line-height: 35px;
    margin-top: 30px;
    margin-bottom: 80px;
  }

  h1 {
    font-size: 14px;
    color: hsl(150, 100%, 66%);
  }



  button {
    position: relative;
    z-index: 1;
    padding: 20px 20px 20px 20px;
    top: 2.4rem;
    background-color: hsl(150, 100%, 66%);
    border: none;
    border-radius: 100%;
    cursor: pointer;
  }

  button:hover {
    box-shadow: 0px 0px 30px hsl(150, 100%, 66%);
  }

  button img {
    margin: 0;
    padding: 0;
    transform: rotate(0deg);
  }

  @media only screen and (max-width: 480px) {
    .advice p {
      font-size: 20px;
      left: clamp(7vw,8vw, 10vw);
    }

    button {
      position: relative;
      z-index: 1;
      padding: 5px 5px 5px 5px;
      left: 25vw;
      top: 1rem;
    } 
  
  }

  @media only screen and (min-width: 480px) and (max-width: 1024px) {
    .advice {
      left: clamp(15vw, 20vw, 30vw);
    }
  }

  @media only screen and (min-width:1130px) {
    .advice {
      width: 500px;
    }
  }
</style>
