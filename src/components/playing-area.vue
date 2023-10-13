<template>
  <div class="container" :class="{ 'no-bg': hideBackground }" ref="container">
    <span class="top-btns" ref="top-btn">
      <button
        class="paper play-btn"
        @click="makeChoice('paper')"
        ref="paperButton"
        :disabled="buttonsDisabled"
      >
        <img src="../assets/images/icon-paper.svg" />
      </button>
      <button
        class="scissors play-btn"
        @click="makeChoice('scissors')"
        ref="scissorsButton"
        :disabled="buttonsDisabled"
      >
        <img src="../assets/images/icon-scissors.svg" />
      </button>
    </span>
    <button
      class="rock play-btn"
      @click="makeChoice('rock')"
      ref="rockButton"
      :disabled="buttonsDisabled"
    >
      <img src="../assets/images/icon-rock.svg" />
    </button>
    <div class="summary" :style="{ display: summaryDisplay }">
      <p>You picked</p>
      <p>the house picked</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      buttonsDisabled: false,
      youPicked: "",
      housePicked: "",
      hideBackground: false,
      summaryDisplay: "none",
    };
  },
  methods: {
    makeChoice(playerChoice) {
      this.summaryDisplay = "flex";
      this.buttonsDisabled = true;
      this.showSecondContainer = true;
      const choices = ["paper", "scissors", "rock"];

      let randomIndex = Math.floor(Math.random() * choices.length);
      let houseChoice = choices[randomIndex];

      while (houseChoice === playerChoice) {
        randomIndex = Math.floor(Math.random() * choices.length);
        houseChoice = choices[randomIndex];
      }

      if (playerChoice === "scissors") {
        this.housePicked = ["rock", "paper"][Math.floor(Math.random() * 2)];
      } else {
        this.housePicked = houseChoice;
      }

      this.$refs[playerChoice + "Button"].classList.add("selected");
      this.$refs[houseChoice + "Button"].classList.add("selected");
      this.$refs["container"].style.flexDirection = "row";

      this.youPicked = playerChoice;
      this.hideBackground = true;
      for (let i = 0; i < choices.length; i++) {
        const choice = choices[i];
        if (choice !== this.youPicked && choice !== this.housePicked) {
          this.$refs[choice + "Button"].style.display = "none";
        } else if (
          this.housePicked == this.youPicked ||
          this.youPicked == this.housePicked
        ) {
          return;
        }
      }
    },
  },
};
</script>
<style scoped>
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  height: 100%;
  background: url("../assets/images/bg-triangle.svg");
  background-repeat: no-repeat;
  background-position: center;
}

.container.no-bg {
  background: none;
}

.container img {
  margin: auto;
  height: 200px;
  width: 200px;
}

.play-btn {
  position: relative;
  border-radius: 50%;
  padding: 15px;
  justify-content: center;
  align-content: center;
  border: none;
  -webkit-box-shadow: inset -4px -40px 6px -26px rgba(66, 68, 90, 0.5);
  -moz-box-shadow: inset -4px -40px 6px -26px rgba(66, 68, 90, 0.5);
  box-shadow: inset -4px -40px 6px -26px rgba(66, 68, 90, 0.5);
  cursor: pointer;
}

.paper {
  background-color: #4766f4;
  display: flex;
}

.scissors {
  background-color: #eda51c;
  display: flex;
}

.rock {
  background-color: #db3152;
  margin-bottom: 50px;
  display: flex;
}

.play-btn img {
  height: 120px;
  width: 120px;
  background-color: white;
  border-radius: 50%;
  padding: 30px;
  -webkit-box-shadow: inset -4px 34px 6px -26px rgba(66, 68, 90, 0.5);
  -moz-box-shadow: inset -4px 34px 6px -26px rgba(66, 68, 90, 0.5);
  box-shadow: inset -4px 34px 6px -26px rgba(66, 68, 90, 0.5);
}

.top-btns {
  display: flex;
  gap: 100px;
  margin-bottom: 50px;
}

.summary {
  position: absolute;
  justify-content: space-around;
  text-align: center;
  width: 100%;
  top: 60%;
  left: 50%;
  transform: translateX(-50%);
}

.summary p {
  color: white;
  text-transform: uppercase;
  font-family: "Barlow Semi Condensed", sans-serif;
  font-size: 20px;
}
</style>
