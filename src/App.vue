<template>
  <main id="main">
    <nav class="navbar">
      <ul>
        <li><a href="#sectionStart">start</a></li>
        <li><a href="#sectionPhoto">photography</a></li>
        <li><a href="#sectionTattoo">tattoo</a></li>
        <li><a href="#sectionAbout">about me</a></li>
      </ul>
    </nav>
    <div class="content">
      <div id="sectionStart" class="section">
        <PromptText class="mainTitle" :text="mainSectionText"/>
      </div>
      <ContentSection id="sectionPhoto" :sectionTitleText="photoSectionText" :imgLeftPath="photoImgLeft" :imgRightPath="photoImgRight"/>
      <ContentSection id="sectionTattoo" :sectionTitleText="tattooSectionText" :imgLeftPath="tattooImgLeft" :imgRightPath="tattooImgRight"/>
      <div id="sectionAbout" class="section">
        <PromptText :text="aboutSectionText"/>
      </div>
    </div>
    <Sketch id="sketch"/>
  </main>
</template>

<script>
import Sketch from "./components/Sketch.vue";
import PromptText from "./components/PromptText.vue";
import ContentSection from "./components/ContentSection.vue";

export default {
  name: "App",
  components: {
    Sketch,
    PromptText,
    ContentSection
  },
  data() {
    return {
      mainSectionText: "Hello,\nI'm Ana Vitoriano.",
      photoSectionText: "photography",
      photoImgLeft: "./public/assets/DSC_0225.jpg",
      photoImgRight: "./public/assets/DSC_9856.jpg",
      tattooSectionText: "tattoo",
      tattooImgLeft: "./public/assets/tattoo1.png",
      tattooImgRight: "./public/assets/tattoo2.png",
      aboutSectionText: "about me"
    };
  },
  mounted() {
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        
        const target = document.querySelector(this.getAttribute('href'));
        target.scrollIntoView({
          behavior: 'smooth'
        });
      });
    });
  }
};
</script>

<style>
body,
html {
  padding: 0;
  margin: 0;
  height: 100%;
  background-color: #050404;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 100vh;
  height: 100vh;
  margin: 0;
  padding-left: 0;
}

#main {
  max-width: 100%;
  position: absolute;
}

.navbar {
  position: fixed;
  z-index: 1000;
}

#sketch {
  position: absolute;
  padding-left: 0;
  margin: 0;
  max-width: 100%;
  background-color: transparent;
}

.content {
  position: absolute;
  z-index: 2;
}

.section {
  z-index: 10;
  height: 100vh;
  margin-left: 5vw;
}

#sectionStart {
  display: table;
  margin-left: 5vw;
}

.mainTitle {
  font-size: 3vw;
  vertical-align: middle;
  display: table-cell;
}

.navbar {
  position: fixed;
  right: 4vw;
  top: 3vh;
}

.navbar ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.navbar ul li {
  display: inline;
  margin-right: 20px;
}

.navbar ul li a {
  color: white;
  text-decoration: none;
  font-family:'Roboto Mono';
  font-size: 1.5vw;
}

.imgContent {
  background-image: url('./assets/first_page.jpg');
}

</style>
