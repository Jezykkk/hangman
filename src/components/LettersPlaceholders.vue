<template>
  <div>
    <ul class="placeholder-list">
      <li class="letter-field" v-for="(field, index) in fields" :key="index">
        <span :class="{'filed-field': field && field !== ' '}">
          <span v-if="checkLetter(field)">{{field}}</span>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'LettersPlaceholders',
  props: {
    fields: Array,
    gL: Set,
    word: String,
    fieldsId: String,
  },
  methods: {
    checkLetter(field) {
      const goodLettersArr = Array.from(this.gL);
      return goodLettersArr.indexOf(field) > -1;
    },
  },
};
</script>

<style scoped lang="scss">
  .placeholder-list{
    list-style: none;
    display: flex;
    flex-direction: row-reverse;
    margin: 0 auto;
    padding: 0;
  }
  .filed-field{
    transition: background-color .4s ease;
    background-color: rgba(83, 85, 93, 0.98);
    display: flex;
    width: 100%;
    height: 100%;
    justify-content: center;
    align-items: center;
    font-family: inherit;
    color: #fff;
    padding-bottom: 5px;
    line-height: 100%;
    text-transform: uppercase;
  }
  .letter-field{
    display: block;
    width: 125px;
    height: 140px;
    box-sizing: border-box;
    border-radius: 10px;
    margin-right: 10px;
    padding: 0;
    overflow: hidden;
    font-size: 92px;
    line-height: 1;
  }
  .letter-field > span:not(.filed-field){
    background-color: #e6e6e7;
    display: inline-block;
    height: 100%;
    width: 100%;
  }
  .letter-field:first-of-type{
    margin-right: 0;
  }
</style>
