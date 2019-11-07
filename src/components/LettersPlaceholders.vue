<template>
  <div>
    <ul class="placeholder-list">
      <li class="letter-field" v-for="(field, index) in fields" :key="index">
        <span :class="{'filed-field': field}">
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
    background-color: #53555d;
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
    width: 125px;
    height: 140px;
    background-color: #e6e6e7;
    border-radius: 10px;
    margin-right: 5px;
    margin-left: 5px;
    overflow: hidden;
    font-family: AllerDisplay, Arial, sans-serif;
    font-size: 92px;
    line-height: 1;
  }
</style>
