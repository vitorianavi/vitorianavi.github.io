<template>
  <main id="main">
    <Sketch id="sketch"/>
    <PromptText class="mainTitle" :text="customText"/>
  </main>
</template>

<script>
import Sketch from "./components/Sketch.vue";
import PromptText from "./components/PromptText.vue";

export default {
  name: "App",
  components: {
    Sketch,
    PromptText
  },
  data() {
    return {
      customText: "Hello,\nI'm Ana Vitoriano."
    };
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
  max-width: 100%;
  height: 100%;
  margin: 0;
  padding-left: 0;
}

#main {
  max-width: 100%;
  position: absolute;
}

#sketch {
  position: absolute;
  padding-left: 0;
  margin: 0;
  max-width: 100%;
  background-color: transparent;
}

.mainTitle {
  font-size: 4vw;
  margin-left: 4vw;
}
</style>
