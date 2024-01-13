<script setup>
import { onMounted, onUnmounted } from "vue";

const updateParallax = () => {
  // Get scroll position
  const scrollY = window.scrollY;
  const windowHeight = window.innerHeight;
  const shapeOne = document.getElementById("shapeOne");
  const shapeTwo = document.getElementById("shapeTwo");
  const portrait = document.getElementById("portrait");
  const helloSection = document.querySelector(".hello-section");
  const webdevSection = document.querySelector(".webdev");
  // Fade out effect
  const startFade = windowHeight * 0.5; // Start fading at half the window height
  const endFade = windowHeight; // Completely fade out at one window height
  let opacity = 1;


  // Adjust these factors to control the speed of the parallax effect
  helloSection.style.transform = `translateY(${scrollY * 1.4}px)`;
  portrait.style.transform = `translateY(${scrollY * 0.2}px)`;
  shapeOne.style.transform = `translateY(${scrollY * 1.7}px)`;
  if (windowHeight > 1400) {
    shapeTwo.style.transform = `translateY(${scrollY * 0.4}px)`;
  } else {
    shapeTwo.style.transform = `translateY(${scrollY * -0.1}px)`;
  }

  if (scrollY > startFade) {
    opacity = 1 - (scrollY - startFade) / (endFade - startFade);
    opacity = Math.max(opacity, 0); // Ensure opacity doesn't go below 0
  }
  webdevSection.style.opacity = opacity;
  helloSection.style.opacity = opacity;
};

onMounted(() => {
  //sets the initial position of the elements
  updateParallax();
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
    </div>
    <div class="webdev">
      <h4>a web developer</h4>
    </div>
    <img src="../assets/imgs/shapeTwo.svg" alt="colorful shape" id="shapeTwo" />

    <section class="aboutSection">
      <div class="container">
        <h3>Webbutvecklarstudent</h3>
        <p>
          Jag är en ambitiös fullstack webbutvecklarstudent vid EC Utbildning i
          Örebro, med examen våren 2024. Min specialisering ligger inom .NET,
          där jag behärskar .NET Core, MVC, Entity Framework och Blazor. Jag har
          även kompetens inom front-end utveckling med React och Vue, samt
          erfarenhet av att arbeta med Git, Azure DevOps och agila metoder. Min
          utbildning har gett mig en stark grund inom HTML, CSS, JavaScript, C#
          och SQL.
          <br />
          <div class="about-links">
            <div>
              <a href="https://github.com/dennisGustavsson" target="_blank">GitHub </a>
              <a href="https://www.linkedin.com/in/dennisgustavsson-hello" target="_blank">LinkedIn</a>
            </div>
            <a
              href="https://ecutbildning.se/utbildningar/webbutvecklare-inom-net/#om-utbildningen"
              target="_blank"
              >Läs mer om min utbildning här.</a
            >
          </div>
        </p>
      </div>
    </section>
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
  }
  .webdev {
    position: relative;
    h4 {
      position: absolute;
      // position: fixed;
      z-index: -2;
      color: white;
      font-weight: 600;
      top: 730px;
      left: 30px;
      @include md {
        left: 400px;
        top: 900px;
      }
      @include xl {
        top: 700px;
        left: auto;
        right: 150px;
        color: black;
        font-size: 40px;
      }
      @include xxl {
        color: white;
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
    z-index: -3;
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

  .aboutSection {
    display: flex;
    justify-content: center;
    .container {
      align-self: center;
      max-width: 700px;
      height: 500px;
      background-color: rgba(233, 233, 233, 0);

      border-radius: 30px;
      backdrop-filter: blur(12px);
      top: auto;
      position: absolute;
      bottom: 200px;
      padding: 2rem;
      margin-inline: 1rem;

      @include md {
        bottom: 350px;
      }

      @include lg {
        top: auto;
        position: absolute;
        bottom: 700px;
        padding: 2rem;
      }
      @include xl {
        bottom: 500px;
      }
      .about-links {
        display: flex;
        justify-content: space-between;
      }
      h3 {
        // color: rgb(185, 100, 206);
        color: whitesmoke;
        font-weight: 600;
        text-shadow: 1px 1px 0px #000000;
      }
      p {
        font-size: 14px;
      }
      a {
        color: #1dcea1;
        font-size: 14px;
      }
    }
  }
}
</style>
