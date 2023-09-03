<template>
  <div>
    <headerVue />
  </div>
</template>

<script>
import headerVue from "./components/header.vue";
export default {
  components: {
    headerVue: headerVue,
  },
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
  padding: 20px;
  height: 100vh;
  width: 100vw;
  background: radial-gradient(circle, hsl(214, 47%, 23%), hsl(237, 49%, 15%));
}
</style>
