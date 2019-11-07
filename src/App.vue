<template>
  <div class="main-app" id="app">
    <div class="top-section">
      <HangManImage :imgClass="imgClass"/>
      <WrongLetters :letters="wrongLetters" :key="wrongId" />
    </div>
    <LettersPlaceholders :fields="comutedFields" :gL="goodLetters" :word="word" :key="fieldsId"/>
    <div v-show="complete" class="word-completed">
      <button @click.prevent="nextWord">Next word</button>
    </div>
    <div v-show="lost" class="game-over">
      <p class="word">{{word}}</p>
      <span>GAME OVER</span>
      <button @click.prevent="newGame">New word</button>
    </div>
  </div>
</template>

<script>
import HangManImage from './components/HangManImage.vue';
import WrongLetters from './components/WrongLetters.vue';
import LettersPlaceholders from './components/LettersPlaceholders.vue';

export default {
  name: 'app',
  components: {
    HangManImage,
    WrongLetters,
    LettersPlaceholders,
  },
  created() {
    window.addEventListener('keyup', this.checkKey);
    this.getWord();
    // this.fetchData();
  },
  data() {
    return {
      reactive: true,
      imgState: 0,
      word: 'test',
      wordsArray: ['polowanie', 'losowanie', 'turysta', 'sekunda', 'personel', 'sterta', 'oliwka', 'konferencja', 'kostka', 'fala', 'cytryna', 'personel', 'ranek', 'futro'],
      goodLetters: new Set(),
      wrongLetters: new Set(),
      fields: [],
      fieldsId: this.getTime(),
      wrongId: `wrong_${this.getTime()}`,
      complete: false,
      lost: false,
    };
  },
  computed: {
    imgClass() {
      return `hangman${this.imgState}`;
    },
    comutedFields() {
      const wordArray = this.word.split('');
      const newArr = Array(11).fill('');
      wordArray.forEach((letter, index) => {
        newArr[wordArray.length - index - 1] = letter;
      });
      return newArr;
    },
    wordUniqueL() {
      const wordSet = new Set();
      this.word.split('').forEach((letter) => {
        wordSet.add(letter);
      });
      return wordSet;
    },
    compuGLetters() {
      return this.goodLetters;
    },
  },
  beforeUpdate() {
    this.isWin();
    this.isGameOVer();
  },
  methods: {
    add() {
      this.imgState += 1;
      this.wrongId = `wrong_${this.getTime()}`;
    },
    getTime() {
      return new Date().getTime();
    },
    fill() {
      this.fieldsId = this.getTime();
    },
    getWord() {
      const random = Math.floor(Math.random() * (this.wordsArray.length));
      this.word = this.wordsArray[random];
    },
    nextWord() {
      this.getWord();
      this.goodLetters.clear();
      this.wrongLetters.clear();
      this.imgState = 0;
      this.fieldsId = this.getTime();
      this.wrongId = `wrong_${this.getTime()}`;
    },
    checkKey(e) {
      if (e.keyCode > 64 && e.keyCode < 91) {
        if (this.word.indexOf(e.key) > -1) {
          this.goodLetters.add(e.key);
          this.fill();
        } else {
          this.wrongLetters.add(e.key);
          this.add();
        }
      }
    },
    isWin() {
      this.complete = false;
      if (this.goodLetters.size === this.wordUniqueL.size) {
        this.complete = true;
        // this.nextWord();
      }
    },
    isGameOVer() {
      this.lost = this.imgState > 11;
      if (this.lost === true) {
        window.removeEventListener('keyup', this.checkKey);
      }
    },
    newGame() {
      window.addEventListener('keyup', this.checkKey);
      this.nextWord();
    },
    // fetchData() {
    //   fetch('https://wordsapiv1.p.rapidapi.com/words/?random=true', {
    //     method: 'GET',
    //     headers: {
    //       'X-Mashape-Key': 'cd13dd1d51mshd93c66d35e2d5c4p13f708jsn7c88284e88b8',
    //       Accept: 'application/json',
    //     },
    //   }).then((response) => {
    //     if (response.status !== 200) {
    //       console.log(`Looks like there was a problem. Status Code: ${response.status}`);
    //       console.log(response);
    //       return;
    //     }
    //     response.json().then((data) => {
    //       console.log(data);
    //     });
    //   }).catch((err) => {
    //     console.log('Fetch Error :-S', err);
    //   });
    // },
  },
};
</script>

<style lang="scss">
@font-face {
  font-family: "AllerDisplay";
  src: url("./assets/AllerDisplay.ttf") format('truetype');
  font-weight: normal;
  font-style: normal;
}
body{
  background-color: #3b4163;
}
button{
  background-color: transparent;
  color: #ffba00;
  border: 3px dashed #ffba00;
  font-size: 24px;
  padding: 38px 90px;
  border-radius: 60px;
  text-transform: uppercase
}
.main-app{
  position: relative;
  background-color: #f5f5f5;
  border-radius: 10px;
  width: 80%;
  max-width: 1600px;
  margin: 0 auto;
  margin-top: 220px;
  padding: 72px;
  box-sizing: border-box;
}
.main-app::before{
  position: absolute;
  content: ' ';
  bottom: 0;
  right: 0;
  border-left: 500px solid transparent;
  border-bottom: 500px solid #4d69fa;
  z-index: 0;
}
.main-app > * {
  z-index: 1;
  position: relative;
}
.game-over, .word-completed{
  position: absolute;
  display: block;
  height: 100%;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: #fff;
  &::before{
    content: ' ';
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: #3b4163;
    opacity: 0.6;
    z-index: -1;
  }
  & > span{
    font-size: 92px;
    color: #fff;
    margin-bottom: 32px;
  }
}
.word{
  font-size: 48px;
  text-decoration: underline;
  text-transform: uppercase;
}
.top-section{
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}
#app {
  font-family: AllerDisplay, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
