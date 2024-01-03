<template>
  <main class="about">
    <img src="../assets/imgs/shapeOne.svg" alt="colorful shape" id="shapeOne" />

    <img src="../assets/imgs/shapeTwo.svg" alt="colorful shape" id="shapeTwo" />
  </main>
</template>

<style scoped lang="scss">
.about {
  height: 100vh !important;
  #shapeOne {
    position: absolute;
    z-index: -1;
    width: 750px;
    top: -100px;
    left: -150px;
    @include md {
      width: 1000px;
      left: -100px;
    }
    @include lg {
      width: 1100px;
      left: -170px;
    }
  }

  #shapeTwo {
    position: absolute;
    top: 600px;
    left: -350px;
    width: 800px;
    z-index: -2;
    @include md {
      width: 1100px;
      left: -100px;
      rotate: 180deg;
    }
    @include lg {
      width: 1200px;
      left: 60%;
      top: 100px;
    }
  }
}
</style>
