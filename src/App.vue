<script setup>
import { ref } from 'vue';

const msg = ref('');
const redScore = ref(0);
const blueScore = ref(0);
const choices = ['ค้อน', 'กรรไกร', 'กระดาษ'];

const redChoiceImages = [
  '/img/kon.svg',
  '/img/kan.svg',
  '/img/paper.svg',
];
const blueChoiceImages = [
  '/img/kan.svg',
  '/img/paper.svg',
  '/img/kon.svg',
];


let redChoiceImage = ref('เสมอ');
let blueChoiceImage = ref('เสมอ');

const playGame = () => {
  const redChoice = choices[Math.floor(Math.random() * choices.length)];
  const blueChoice = choices[Math.floor(Math.random() * choices.length)];


  redChoiceImage.value = getRandomImage(redChoiceImages);
  blueChoiceImage.value = getRandomImage(blueChoiceImages);


  if (redChoice === blueChoice) {

  } else if (
    (redChoice === 'ค้อน' && blueChoice === 'กรรไกร') ||
    (redChoice === 'กรรไกร' && blueChoice === 'กระดาษ') ||
    (redChoice === 'กระดาษ' && blueChoice === 'ค้อน')
  ) {
  
    redScore.value++;
  } else {

    blueScore.value++;
  }
};

const resetScores = () => {
  redScore.value = 0;
  blueScore.value = 0;
  redChoiceImage.value = '';
  blueChoiceImage.value = '';
};

const getRandomImage = (imageArray) => {
  return imageArray[Math.floor(Math.random() * imageArray.length)];
};
</script>

<template>
<div class="box_img">
<img src="/img/เปา copy.png" class="logo" alt="" />
</div>

<div>
    <h1>{{ msg }}</h1>
    <div class="team">
      <div class="red-team">
        <img :src="redChoiceImage" alt="Red Team Choice">
        <p>คะแนนฝ่ายแดง: {{ redScore }}</p>
      </div>
      <div class="blue-team">
        <img :src="blueChoiceImage" alt="Blue Team Choice">
        <p>คะแนนฝ่ายน้ำเงิน: {{ blueScore }}</p>
      </div>
    </div>
    <div class="card">
      <button type="button" @click="playGame"> เกม เปา........ยิ้งฉุบบบ</button>
      <button type="button" @click="resetScores">รีเซตคะแนน</button>
    </div>
  </div>

  <div>
    
    
 
</div>
  
  
</template>

<style scoped>
.read-the-docs {
  color: #888;
}

.team {
  display: flex;
  justify-content: space-around;
}

.red-team, .blue-team {
  text-align: center;
}

.team img {
  max-width: 100px;
  height: auto;
}

.card {
  margin-top: 20px;
  display: flex;
  justify-content: center;
}

.card button {
  margin: 0 10px;
}

:root {
  font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;

  color-scheme: light dark;
  color: rgba(255, 255, 255, 0.87);
  background-color: #242424;

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-text-size-adjust: 100%;
}

a {
  font-weight: 500;
  color: #646cff;
  text-decoration: inherit;
}
a:hover {
  color: #535bf2;
}

a {
  font-weight: 500;
  color: #646cff;
  text-decoration: inherit;
}
a:hover {
  color: #535bf2;
}

body {
  margin: 0;
  display: flex;
  place-items: center;
  min-width: 320px;
  min-height: 100vh;
  margin-top: 20px;
  
}

h1 {
  font-size: 3.2em;
  line-height: 1.1;
}

button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  background-color: #1a1a1a;
  cursor: pointer;
  transition: border-color 0.25s;
}
button:hover {
  border-color: #646cff;
}
button:focus,
button:focus-visible {
  outline: 4px auto -webkit-focus-ring-color;
}

.card {
  padding: 2em;
}

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  text-align: center;
}

@media (prefers-color-scheme: light) {
  * {
   background-image: url();
   background-color: rgb(0, 195, 255);
    
  }
  a:hover {
    color: #4f54b1;
  }
  button {
    background-color: #f9f9f9;
  }
}

.logo {
  height: 20em;
  will-change: filter;
  transition: filter 300ms;
  transform: rotate(90deg);
  margin-left: 600px

}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

</style>
