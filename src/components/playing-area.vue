<template>
  <div class="container">
    <img src="../assets/images/bg-triangle.svg" />
    <button class="paper"></button>
    <button class="scissors"></button>
    <button class="rock"></button>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.container img {
  margin: auto;
  height: 200px;
  width: 200px;
}
</style>
