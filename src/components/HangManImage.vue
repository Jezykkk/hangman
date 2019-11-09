<template>
  <div :class="imgClass">
    <div class="gallows">
      <div class="gallows-horizontal"/>
      <div class="gallows-vertical"/>
    </div>
    <div class="person">
      <div class="head">
        <div class="ear-left"/>
        <div class="ear-right"/>
        <div class="face-main-shade">
          <div class="vein"/>
          <div class="head-hair">
            <div class="hair-left"/>
            <div class="hair-right"/>
          </div>
          <div class="eyes">
            <div class="left-eye"/>
            <div class="right-eye"/>
          </div>
          <div class="left-chick"/>
          <div class="nose"/>
          <div class="right-chick"/>
        </div>
        <div class="mouth"/>
      </div>
      <div class="neck"/>
      <div class="torso">
        <div class="left-torso"/>
        <div class="right-torso"/>
      </div>
      <div class="left-arm"/>
      <div class="left-hand"/>
      <div class="right-arm"/>
      <div class="right-hand"/>
      <div class="left-leg"/>
      <div class="right-leg"/>
      <div class="left-feet"/>
      <div class="right-feet"/>
    </div>
    <div class="hangman-img hangman-0" :class="imgClass"/>
  </div>
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
$skin-color1: #ebc48e;
$skin-color2:  #ebc58f;
$light-green: #8ac657;
$dark-green: #4ea06a;
$dark-blue: #3c5a92;
$gray: #a0a0a0;
$dark-gray: #53555d;

.gallows-horizontal{
  width: 241px;
  height: 30px;
  background-color: $dark-gray;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
  position: relative;
  left: -74px;
}
.gallows-vertical{
  height: 42px;
  width: 30px;
  background-color: $dark-gray;
  position: relative;
  left: 107px;
  z-index: 0;
}
.person{
  position: relative;
  width: 284px;
  height: 570px;
  margin-top: -3px;
  margin-bottom: 58px;
  margin-left: -18px;
  z-index: 1;
}
.head{
  width: 144px;
  height: 212px;
  background-color: $skin-color1;
  border-radius: 80px;
  position: absolute;
  left: 50%;
  transform: translate(-50%, 0);
  z-index: 1;
}
.head-hair{
  width: 100%;
  height: 100px;
  border-top-right-radius: 80px;
  border-top-left-radius: 80px;
  background-color: transparent;
  overflow: hidden;
}
.left-eye{
  position: relative;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: #3e3e3f;
  border: 1px solid #192231;
  box-shadow: 0 0 0 1px #ffe797;
  left: 34px;
  top: -7px;
  z-index: 1;
}
.right-eye{
  position: relative;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: #3e3e3f;
  border: 1px solid #192231;
  box-shadow: 0 0 0 1px #ffe797;
  left: 97px;
  top: -21px;
  z-index: 1;
}
.ear-left{
  position: absolute;
  left: -24px;
  top: 83px;
  width: 40px;
  height: 36px;
  border-top-left-radius: 50%;
  border-bottom-left-radius: 50%;
  background-color: #fecd8a;
  &::before{
    content: ' ';
    position: relative;
    left: 14px;
    top: 10px;
    border: 1px solid #feb769;
    border-top-left-radius: 40px;
    border-bottom-left-radius: 40px;
    display: block;
    width: 16px;
    height: 15px;
    background-color: #febd71;
  }
}
.ear-right{
  position: absolute;
  right: -24px;
  top: 83px;
  width: 40px;
  height: 36px;
  border-top-right-radius: 50%;
  border-bottom-right-radius: 50%;
  background-color: #fecd8a;
  &::before{
    content: ' ';
    position: relative;
    right: -8px;
    top: 10px;
    border: 1px solid #feb769;
    border-top-right-radius: 40px;
    border-bottom-right-radius: 40px;
    display: block;
    width: 16px;
    height: 15px;
    background-color: #febd71;
  }
  &::after{
    content: ' ';
    position: relative;
    right: -19px;
    top: 15px;
    border: 1px solid $gray;
    border-top: 1px solid #8a95a5;
    border-radius: 50%;
    display: block;
    width: 6px;
    height: 6px;
    background-color: $gray;
  }
}
.vein{
  height: 28px;
  width: 18px;
  background-image: url("../assets/vein.png");
  position: absolute;
  top: 37px;
  left: 24px;
}
.hair-left{
  background-color: $skin-color2;
  height: 250px;
  width: 250px;
  position: relative;
  border-radius: 50%;
  top: -110px;
  left: -227px;
}
.hair-right{
  background-color: $skin-color2;
  height: 250px;
  width: 250px;
  position: relative;
  border-radius: 50%;
  top: -359px;
  right: -121px;
}
.face-main-shade{
  width: 100%;
  height: 120px;
  background-color: #fece8a;
  position: relative;
  border-top-right-radius: 80px;
  border-top-left-radius: 80px;
}
.left-chick{
  position: absolute;
  width: 60px;
  height: 30px;
  background-color: #fece8a;
  bottom: -9px;
  left: 11px;
  transform: rotate(-18deg);
  border-radius: 11px;
  z-index: 0;
}
.right-chick{
  position: absolute;
  width: 70px;
  height: 20px;
  background-color: #fece8a;
  bottom: -5px;
  right: 13px;
  transform: rotate(14deg);
  border-radius: 8px;
  z-index: 0;
}
.nose{
  position: absolute;
  bottom: -14px;
  left: 50%;
  transform: translate(-50%, 0);
  width: 20px;
  height: 30px;
  margin-left: 1px;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  background-color: #fece8a;
}
.mouth{
  width: 36px;
  height: 19px;
  background-color: #fff;
  border: 1px solid #e7bb7a;
  border-top-left-radius: 36px;
  border-top-right-radius: 36px;
  border-bottom: 1px solid #fff;
  position: relative;
  left: 54px;
  top: 16px;
  box-sizing: border-box;
  &::before{
    content: ' ';
    position: absolute;
    border: 1px solid $gray;
    border-radius: 50%;
    display: block;
    width: 8px;
    height: 8px;
    background-color: $gray;
    bottom: 0;
    left: -11px;
    box-sizing: border-box;
    box-shadow: 0 0 0 1px #f9cc8b;
  }
}
.neck{
  width: 46px;
  height: 40px;
  border-bottom-left-radius: 14px;
  border-bottom-right-radius: 14px;
  background-color: #fece8a;
  position: relative;
  left: 48px;
  top: 208px;
  z-index: 0;
  left: 50%;;
  transform: translate(-50%, 0);
}
.torso{
  width: 104px;
  height: 165px;
  border-radius: 14px;
  background-color: $dark-blue;
  position: absolute;
  left: 50%;
  top: 228px;
  display: flex;
  transform: translate(-50%, 0);
  overflow: hidden;
}
.left-torso{
  flex: 1;
  background-color: $light-green;
  height: 122px;
}
.right-torso{
  flex: 1;
  background-color: $dark-green;
  height: 122px;
}
.left-arm{
  width: 136px;
  height: 47px;
  border-radius: 10px;
  transform: rotate(-45deg);
  background-color: $light-green;
  position: absolute;
  top: 268px;
  left: -1px;
  z-index: 1;
}
.left-hand{
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background-color: #fece8a;
  position: absolute;
  left: 3px;
  bottom: 213px;
  z-index: 0;
}
.right-arm{
  width: 136px;
  height: 47px;
  border-radius: 10px;
  transform: rotate(45deg);
  background-color: $dark-green;
  position: absolute;
  top: 268px;
  right: -1px;
  z-index: 1;
}
.right-hand{
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background-color: #fece8a;
  position: absolute;
  right: 3px;
  bottom: 213px;
  z-index: 0;
}
.left-leg{
  width: 50px;
  height: 182px;
  transform: rotate(12deg);
  background-color: $dark-blue;
  border-radius: 10px;
  position: absolute;
  top: 371px;
  left: 74px;
  z-index: 1;
}
.right-leg{
  width: 50px;
  height: 182px;
  transform: rotate(-12deg);
  background-color: $dark-blue;
  border-radius: 10px;
  position: absolute;
  top: 371px;
  right: 74px;
  z-index: 1;
}
.left-feet{
  width: 82px;
  height: 29px;
  transform: rotate(8deg);
  border-radius: 7px;
  background-color: #fece8a;
  position: absolute;
  bottom: 5px;
  left: 18px;
  z-index: 0;
}
.right-feet{
  width: 82px;
  height: 29px;
  transform: rotate(-8deg);
  border-radius: 7px;
  background-color: #fece8a;
  position: absolute;
  bottom: 5px;
  right: 18px;
  z-index: 0;
}
  .head,
  .left-arm,
  .right-arm,
  .neck,
  .left-hand,
  .right-hand,
  .left-leg,
  .right-leg,
  .torso,
  .left-feet,
  .right-feet{
    transition: .2s opacity ease-in;
  }
.hangman0{
  .gallows-horizontal,
  .gallows-vertical,
  .head,
  .left-arm,
  .right-arm,
  .neck,
  .left-hand,
  .right-hand,
  .left-leg,
  .right-leg,
  .torso,
  .left-feet,
  .right-feet{
    visibility: hidden;
    opacity: 0;
  }
}
.hangman1{
  .gallows-horizontal,
  .gallows-vertical,
  .left-arm,
  .right-arm,
  .neck,
  .left-hand,
  .right-hand,
  .left-leg,
  .right-leg,
  .torso,
  .left-feet,
  .right-feet{
    opacity: 0;
  }
}
.hangman2{
  .gallows-horizontal,
  .gallows-vertical,
  .left-arm,
  .right-arm,
  .left-hand,
  .right-hand,
  .left-leg,
  .right-leg,
  .torso,
  .left-feet,
  .right-feet{
    opacity: 0;
  }
}
.hangman3{
  .gallows-horizontal,
  .gallows-vertical,
  .left-arm,
  .right-arm,
  .left-hand,
  .right-hand,
  .left-leg,
  .right-leg,
  .left-feet,
  .right-feet{
    opacity: 0;
  }
}
.hangman4{
  .gallows-horizontal,
  .gallows-vertical,
  .left-arm,
  .left-hand,
  .right-hand,
  .left-leg,
  .right-leg,
  .left-feet,
  .right-feet{
    opacity: 0;
  }
}
.hangman5{
  .gallows-horizontal,
  .gallows-vertical,
  .left-hand,
  .right-hand,
  .left-leg,
  .right-leg,
  .left-feet,
  .right-feet{
    opacity: 0;
  }
}
.hangman6{
  .gallows-horizontal,
  .gallows-vertical,
  .left-hand,
  .left-leg,
  .right-leg,
  .left-feet,
  .right-feet{
    opacity: 0;
  }
}
.hangman7{
  .gallows-horizontal,
  .gallows-vertical,
  .left-leg,
  .right-leg,
  .left-feet,
  .right-feet{
    opacity: 0;
  }
}
.hangman8{
  .gallows-horizontal,
  .gallows-vertical,
  .left-leg,
  .left-feet,
  .right-feet{
    opacity: 0;
  }
}
.hangman9{
  .gallows-horizontal,
  .gallows-vertical,
  .left-feet,
  .right-feet{
    opacity: 0;;
  }
}
.hangman10{
  .gallows-horizontal,
  .gallows-vertical,
  .left-feet{
    opacity: 0;
  }
}
.hangman11{
  .gallows-horizontal,
  .gallows-vertical{
    opacity: 0;
  }
}
</style>
