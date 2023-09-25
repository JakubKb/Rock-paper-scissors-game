<template>
  <div class="container" :class="{ 'no-bg': hideBackground }">
    <span class="top-btns">
      <button
        class="paper play-btn"
        :style="{ display: paperBtnDisplay }"
        @click="makeChoice('paper')"
        ref="paperButton"
        :disabled="buttonsDisabled"
      >
        <img src="../assets/images/icon-paper.svg" />
      </button>
      <button
        class="scissors play-btn"
        :style="{ display: scissorsBtnDisplay }"
        @click="makeChoice('scissors')"
        ref="scissorsButton"
        :disabled="buttonsDisabled"
      >
        <img src="../assets/images/icon-scissors.svg" />
      </button>
    </span>
    <button
      class="rock play-btn"
      :style="{ display: rockBtnDisplay }"
      @click="makeChoice('rock')"
      ref="rockButton"
      :disabled="buttonsDisabled"
    >
      <img src="../assets/images/icon-rock.svg" />
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      paperBtnDisplay: "flex",
      scissorsBtnDisplay: "flex",
      rockBtnDisplay: "flex",
      buttonsDisabled: false,
      youPicked: "",
      housePicked: "",
      hideBackground: false,
    };
  },
  methods: {
    makeChoice(playerChoice) {
      this.buttonsDisabled = true;
      const choices = ["paper", "scissors", "rock"];

      const randomIndex = Math.floor(Math.random() * choices.length);
      const houseChoice = choices[randomIndex];

      if (playerChoice === "scissors") {
        this.housePicked = ["rock", "paper"][Math.floor(Math.random() * 2)];
      } else {
        this.housePicked = houseChoice;
      }

      this.youPicked = playerChoice;
      this.hideBackground = true;

      choices.forEach((choice) => {
        this.$refs[choice + "Button"].classList.remove("selected");
        if (choice !== playerChoice && choice !== this.housePicked) {
          this.$refs[choice + "Button"].style.display = "none";
        }
      });

      this.$refs[this.youPicked + "Button"].classList.add("selected");
      this.$refs[this.housePicked + "Button"].classList.add("selected");
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
  display: flex;
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
}

.scissors {
  background-color: #eda51c;
}

.rock {
  background-color: #db3152;
  margin-bottom: 50px;
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

.selected {
  -webkit-box-shadow: -4px 34px 6px -26px rgba(66, 68, 90, 0.5);
  -moz-box-shadow: -4px 34px 6px -26px rgba(66, 68, 90, 0.5);
  box-shadow: -4px 34px 6px -26px rgba(66, 68, 90, 0.5);
}
</style>
