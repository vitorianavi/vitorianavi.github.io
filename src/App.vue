<template>
  <main id="main">
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-nav>
        <b-nav-item href="#">About</b-nav-item>
        <b-nav-item href="#" disabled>Disabled</b-nav-item>
      </b-navbar-nav>
    </b-navbar>
    <div id="title">
      <img src="./assets/ana_vitoriano3.png"/>
    </div>
    <Sketch id="sketch"/>
  </main>
</template>

<script>
import Sketch from "./components/Sketch.vue";

export default {
  name: "App",
  components: {
    Sketch
  }
};
</script>

<style>
body,
html {
  padding: 0;
  margin: 0;
  height: 100%;
  background-color: #333333;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 100%;
  height: 100%;
  margin: 0;
}

#main {
  max-width: 100%;
  background-color: transparent;
}

#title {
  max-width: 100%;
  position: absolute;
  background-color: transparent;
  position: fixed;
  bottom: 0px;
  margin-top: 2%;
  max-width: 100%;
  margin-left: 0;
  height: auto;
}

#sketch {
  position: absolute;
  padding-left: 0;
  margin: 0;
  max-width: 100%;
  background-color: transparent;
}
</style>
