<template>
<div class="wrong-letters-container">
  <p class="title">You missed:</p>
  <ul class="wrong-letters">
    <li v-for="(letter, index) in letters" :key="index">
      {{letter}}
    </li>
  </ul>
 </div>
</template>

<script>
export default {
  name: 'WrongLetters',
  props: {
    letters: Set,
  },
};
</script>

<style scoped lang="scss">
.wrong-letters-container{
  width: 50%;
  text-align: left;
}
.wrong-letters-container .title{
  font-size: 24px;
  color: #53555d;
  text-transform: uppercase;
}
.wrong-letters{
  text-transform: uppercase;
  font-size: 92px;
  color: #4d69fa;
  list-style-type: none;
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  padding: 0;
  margin: 0;
}
</style>
