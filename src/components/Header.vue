<template>
  <div class="header">
    <h1>Souf<span>|/</span>MathQuiz</h1><small>By Soufiane M'channa</small>
  </div>
</template>

<script>
export default {};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Anton&display=swap");
.header {
  width: 100vw !important;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #00adb5;
  color: white;
}
h1 {
  letter-spacing: 3.5px;
  font-family: "Anton", sans-serif;
  font-weight: 500;
  cursor: pointer;
}
h1 > span {
  opacity: 0.8;
}
@media screen  and (max-width: 700px) {
  h1 {
    letter-spacing: 2px;
  }
}
</style>
