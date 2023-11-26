<template>
  <div class="container">
    <button class="rules-btn" @click="openRules">Rules</button>
  </div>
  <rules :style="{ display: rulesDisplay }" @close="closeRules" />
</template>

<script>
import rules from "./rules.vue";
export default {
  components: {
    rules: rules,
  },
  data() {
    return {
      rulesDisplay: "none",
    };
  },
  methods: {
    openRules() {
      if (this.rulesDisplay === "none") {
        this.rulesDisplay = "flex";
      }
    },
    closeRules() {
      this.rulesDisplay = "none";
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  margin-bottom: 100px;
}
.rules-btn {
  background: none;
  border: 2px solid hsl(217, 16%, 45%);
  font-size: 25px;
  padding: 5px 35px;
  text-transform: uppercase;
  color: #fff;
  font-family: "Barlow Semi Condensed", sans-serif;
  font-weight: 600;
  border-radius: 7px;
  cursor: pointer;
}

@media (min-width: 601px) {
  .container {
    position: absolute;
    bottom: -70px;
    right: 25px;
  }
}
</style>
