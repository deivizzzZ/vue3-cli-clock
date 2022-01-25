<script setup>
import DigitalClock from "./components/DigitalClock.vue";
</script>

<template>
  <div class="container">
    <h1>Digital Clock</h1>
    <div class="container-clock">
      <DigitalClock colorClock="blue" timeZone="America/New_York" />
      <DigitalClock colorClock="yellow" />
      <DigitalClock colorClock="red" timeZone="Europe/Moscow" />
    </div>
  </div>
</template>

<style lang="scss">
body {
  padding: 0;
  margin: 0;
}
@import url("https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap");
.container {
  margin: 0 auto;
  width: 800px;
}
.container h1 {
  font-family: "Orbitron", sans-serif;
  text-align: center;
}
.container-clock {
  display: flex;
  border: 3px solid black;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
    rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
}
</style>
