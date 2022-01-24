<script>
export default {
  name: "DigitalClock",
  props: {
    colorClock: String
  },
  data() {
    return {
      hours: 0,
      minutes: 0,
      seconds: 0,
      pm: false,
      pmHours: false
    };
  },
  mounted() {
    setInterval(() => this.setTime(), 1000);
  },
  methods: {
    setTime() {
      const date = new Date();
      this.hours = date.getHours();
      this.minutes = date.getMinutes();
      this.seconds = date.getSeconds();
      this.pmHours = this.hours > 12;
    },
    timeFormat(time) {
      return time < 10 ? "0" + time : time;
    },
    ampm(hour) {
      hour = hour % 12;
      hour = hour || 12;
      return hour;
    },
    toggle() {
      this.pm = !this.pm;
    },

  },

};
</script>

<template>
  <div class="container" :class="colorClock">
    <div class="lcd">
      <div v-if="this.pm" class="hours">{{ this.timeFormat(this.ampm(hours)) }}</div>
      <div v-else class="hours">{{ this.timeFormat(hours) }}</div>
      <div class="divider">:</div>
      <div class="minutes">{{ this.timeFormat(minutes) }}</div>
      <div class="divider">:</div>
      <div class="seconds">{{ this.timeFormat(seconds) }}</div>
      <div v-if="this.pm" class="am-pm">{{ this.pmHours ? "PM" : "AM" }}</div>
    </div>
    <button @click="this.toggle">{{ this.pm ? "24H" : "AM/PM" }}</button>
  </div>
</template>

<style scoped>
.container {
  border-right: 3px solid black;
}
.container:last-of-type {
  border-right: none;
}
.lcd {
  font-family: "Orbitron", sans-serif;
  font-size: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
.red {
  background-color: red;
  color: yellow;
}
.blue {
  background-color: blue;
  color: white;
}
.yellow {
  background-color: yellow;
  color: blue;
}

button {
  background-color: white;
  color: black;
  border-radius: 5px;
  border: 1px solid black;
  display: block;
  padding: 5px 25px;
  margin: 10px auto;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.1s;
}
button:hover {
  transform: scale(1.05);
  background-color: rgb(212, 212, 212);
}
.am-pm {
  margin-left: 10px;
}
</style>
