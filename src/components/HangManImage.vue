<template>
  <div class="hangman-img hangman-0" :class="imgClass"/>
</template>

<script>
export default {
  name: 'HangManImage',
  props: {
    imgClass: String,
  },
};
</script>

<style scoped lang="scss">
.hangman-img{
  height: 488px;
  width: 288px;
  background-image: url("../assets/flow.png");
  background-position: 0 0;
  background-repeat: no-repeat;
}

@mixin translateImg($x, $y) {
  @if $y {
    background-position: -288px * ($x - 6) -488px;
  }
  @else{
    background-position: -288px * $x 0;
  }
}
.hangman1{
 @include translateImg(1, null);
}
.hangman2{
  @include translateImg(2, null);
}
.hangman3{
  @include translateImg(3, null);
}
.hangman4{
  @include translateImg(4, null);
}
.hangman5{
  @include translateImg(5, null);
}
.hangman6{
  @include translateImg(6, 1);
}
.hangman7{
  @include translateImg(7, 1);
}
.hangman8{
  @include translateImg(8, 1);
}
.hangman9{
  @include translateImg(9, 1);
}
.hangman10{
  @include translateImg(10, 1);
}
.hangman11{
  @include translateImg(11, 1);
}
.hangman12{
  @include translateImg(11, 1);
}
.hangman12::before{
  content: ' ';
  position: absolute;
  top: -32px;
  left: -72px;
  background-image: url("../assets/gallows.png");
  background-repeat: no-repeat;
  background-position: top right;
  width: 260px;
  height: 200px;
  display: block;
}
</style>
