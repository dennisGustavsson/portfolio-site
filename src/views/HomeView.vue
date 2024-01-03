<script setup>
import { onMounted, onUnmounted } from "vue";

const updateParallax = () => {
  const scrollY = window.scrollY;
  const windowHeight = window.innerHeight;
  const shapeOne = document.getElementById("shapeOne");
  const shapeTwo = document.getElementById("shapeTwo");
  const portrait = document.getElementById("portrait");
  const helloSection = document.querySelector(".hello-section");

  // Adjust these factors to control the speed of the parallax effect
  helloSection.style.transform = `translateY(${scrollY * 1.4}px)`;
  portrait.style.transform = `translateY(${scrollY * 0.2}px)`;
  shapeOne.style.transform = `translateY(${scrollY * 1.7}px)`;
  if (windowHeight > 1400) {
    shapeTwo.style.transform = `translateY(${scrollY * 0.4}px)`;
  } else {
    shapeTwo.style.transform = `translateY(${scrollY * -0.1}px)`;
  }

  // Fade out effect
  const startFade = windowHeight * 0.5; // Start fading at half the window height
  const endFade = windowHeight; // Completely fade out at one window height
  let opacity = 1;

  if (scrollY > startFade) {
    opacity = 1 - (scrollY - startFade) / (endFade - startFade);
    opacity = Math.max(opacity, 0); // Ensure opacity doesn't go below 0
  }

  helloSection.style.opacity = opacity;
};

onMounted(() => {
  window.addEventListener("scroll", updateParallax);
});

onUnmounted(() => {
  window.removeEventListener("scroll", updateParallax);
});
</script>

<template>
  <main class="container-fluid">
    <img src="../assets/imgs/shapeOne.svg" alt="colorful shape" id="shapeOne" />
    <img
      id="portrait"
      src="../assets/imgs/Dennis.jpg"
      alt="Portrait of Dennis"
    />
    <div class="hello-section">
      <h2>Hi, I'm <span>Dennis!</span></h2>
      <h4>a web developer</h4>
    </div>
    <img src="../assets/imgs/shapeTwo.svg" alt="colorful shape" id="shapeTwo" />
  </main>
</template>

<style lang="scss">
.container-fluid {
  margin: 0;
  padding: 0;
  position: relative;
  overflow: hidden;
  min-height: 200vh;
  #portrait {
    height: 300px;
    width: 300px;
    border-radius: 50%;
    z-index: 0;
    position: absolute;
    top: 70px;
    left: 40px;
    @include lg {
      left: 44%;
      top: 140px;
      width: 400px;
      height: 400px;
    }

    @include xl {
      left: 64%;
      top: 140px;
      width: 400px;
      height: 400px;
    }
    @include xxxl {
      left: auto;
      right: 30%;
    }
  }

  .hello-section {
    position: absolute;
    top: 390px;
    left: 110px;
    @include xxl {
      left: 550px;
      top: 260px;
    }
    h2 {
      font-size: 70px;
      color: white;
      z-index: 4;
      @include xl {
        font-size: 70px;
      }
      @include xxl {
        font-size: 100px;
      }
      span {
        font-size: 70px;
        font-weight: 600;
        color: $text-color-primary;
        @include lg {
          text-shadow: 0px 0px 6px #e7e7e79a;
          font-size: 100px;
        }
      }
    }
    h4 {
      position: fixed;
      color: white;
      font-weight: 600;
      top: 350px;
      left: -70px;
      @include md {
        left: 200px;
      }
      @include xl {
        left: auto;
        right: 100px;
        color: black;
      }
    }
  }

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
      top: 400px;
    }
    @include xxxl {
      left: auto;
      right: -10%;
    }
  }
}
</style>
