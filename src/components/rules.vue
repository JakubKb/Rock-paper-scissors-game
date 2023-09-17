<template>
  <div class="container">
    <div class="rules-wrapper">
      <h2>Rules</h2>
      <img
        src="../assets/images/image-rules.svg"
        alt="rules: paper beats rock, rock beats scissors and scissors beat paper"
      />
      <button>
        <img
          src="../assets/images/icon-close.svg"
          alt="X icon"
          @click="closeRules"
        />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    closeRules() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.container {
  position: absolute;
  height: 100vh;
  width: 100vw;
  background-color: #fff;
  display: flex;
  flex-direction: column;
}

h2 {
  font-family: "Barlow Semi Condensed", sans-serif;
  text-transform: uppercase;
  font-size: 40px;
  color: #404764;
}

img {
  height: 350px;
}

.rules-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  height: 100vh;
}

button {
  background: none;
  border: none;
  cursor: pointer;
}

button img {
  height: 30px;
}
</style>
