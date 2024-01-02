<script setup>
import { onMounted, onUnmounted } from "vue";

const updateParallax = () => {
  const scrollY = window.scrollY;
  const shapeOne = document.getElementById("shapeOne");
  const shapeTwo = document.getElementById("shapeTwo");
  const portrait = document.getElementById("portrait");
  const helloSection = document.querySelector(".hello-section");

  // Adjust these factors to control the speed of the parallax effect
  helloSection.style.transform = `translateY(${scrollY * 1.4}px)`;
  portrait.style.transform = `translateY(${scrollY * 0.2}px)`;
  shapeOne.style.transform = `translateY(${scrollY * 1.7}px)`;
  shapeTwo.style.transform = `translateY(${scrollY * 0.2}px)`;
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
    z-index: 3;
    position: absolute;
    top: 70px;
    left: 40px;

    @include lg {
      left: 64%;
      top: 140px;
      width: 400px;
      height: 400px;
    }
  }

  .hello-section {
    position: absolute;
    top: 390px;
    left: 110px;
    @include lg {
      left: 550px;
      top: 260px;
    }
    h2 {
      font-size: 70px;
      color: white;
      @include lg {
        font-size: 100px;
      }
      span {
        font-size: 70px;
        font-weight: 600;
        color: $text-color-primary;
        @include lg {
          font-size: 100px;
        }
      }
    }
    h4 {
      position: inherit;
      color: white;
      font-weight: 600;
      top: 350px;
      left: -70px;
    }
  }

  #shapeOne {
    position: absolute;
    z-index: -1;
    width: 750px;
    top: -100px;
    left: -150px;
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
    @include lg {
      width: 1200px;
      left: 60%;
      top: 100px;
    }
  }
}
</style>
