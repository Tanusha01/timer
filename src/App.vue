<template>
  <TimerComponent />
</template>

<script setup>
import TimerComponent from './components/TimerComponent.vue'
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.buttonAddNew {
  width: 225px;
  height: 120px;
  background: #696969;
}
.newTimer {
  width: 225px;
  height: 120px;
  background: #696969;
  margin: 20px 0;
}
button {
  outline: none;
  background: none;
  border: none;
}
.line {
  border: 1px solid #9e9e9e;
  margin-top: 20px;
}
.timer {
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 22px;
  font-family: 'Gotham Pro';
  font-style: normal;
  font-weight: 400;
  font-size: 22px;
  line-height: 21px;
  color: #9e9e9e;
}
.functional {
  padding-top: 20px;
}
.square {
  margin-left: 48px;
}

.functional svg {
  color: #9e9e9e;
}

.color .timer {
  color: #fff;
}

.color .line {
  border-color: #fff;
}

.color svg {
  color: #fff;
}
.allTimers {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 20px;
  width: 720px;
  margin: 0 auto;
}
@media (max-width: 800px) {
  .allTimers {
    width: 500px;
  }
}
@media (max-width: 510px) {
  .allTimers {
    width: 300px;
  }
}
</style>
