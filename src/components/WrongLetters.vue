<template>
  <div>
    <ul>
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
  created() {
    console.log('zzz', this.letters);
  },
};
</script>

<style scoped lang="scss">

</style>
