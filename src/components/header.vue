<template>
  <span class="container-wrapper">
    <div class="container">
      <ul>
        <li>Rock</li>
        <li>Paper</li>
        <li>Scissors</li>
      </ul>
      <div class="score">
        <span class="score-text">
          <p>Score</p>
          <h3>12</h3>
        </span>
      </div>
    </div>
  </span>
</template>

<script>
export default {};
</script>

<style scoped>
.container {
  color: #fff;
  border: 3px solid hsl(217, 16%, 45%);
  padding: 10px;
  border-radius: 7px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

.container-wrapper {
  padding: 20px;
}

.container ul {
  font-size: 27px;
  text-transform: uppercase;
  list-style: none;
  font-family: "Barlow Semi Condensed", sans-serif;
  font-weight: 700;
  display: flex;
  flex-direction: column;
  line-height: 21px;
  padding: 10px;
}

.container .score {
  background-color: #fff;
  color: hsl(229, 64%, 46%) !important;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  width: 90px;
  height: 80px;
  border-radius: 7px;
}

.score-text {
  text-align: center;
  font-family: "Barlow Semi Condensed", sans-serif;
  font-weight: 600;
  text-transform: uppercase;
}

.score-text h3 {
  font-size: 45px;
  color: hsl(229, 25%, 31%) !important;
}
</style>
