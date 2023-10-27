<template>
  <div class="app">
    <headerVue :score="score" />
    <playingAreaVue @update-score="updateScore" />
    <rulesBtn />
  </div>
</template>

<script>
import headerVue from "./components/header.vue";
import playingAreaVue from "./components/playing-area.vue";
import rulesBtn from "./components/rules-btn.vue";

export default {
  components: {
    headerVue: headerVue,
    playingAreaVue: playingAreaVue,
    rulesBtn: rulesBtn,
  },
  data() {
    return {
      score: 0,
    };
  },
  methods: {
    updateScore() {
  
      this.score++; 
    }
  }
};
</script>


<style>
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  overflow: hidden;
  height: 100vh;
  width: 100vw;
  background: radial-gradient(circle, hsl(214, 47%, 23%), hsl(237, 49%, 15%));
}

.app {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>
