<template>
  <h1>Секундомеры</h1>
  <div class="allTimers">
    <div
      class="newTimer"
      :class="{ color: timer.running }"
      v-for="(timer, index) in timers"
      :key="index"
    >
      <div class="timer">{{ formatTime(timer.seconds) }}</div>
      <div class="line"></div>
      <div class="functional">
        <button v-if="!timer.running" @click="startTimer(timer)">
          <svg
            width="17"
            height="20"
            viewBox="0 0 17 20"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path d="M0 20V0L17 10L0 20Z" fill="currentColor" />
          </svg>
        </button>
        <button v-if="timer.running" @click="pauseTimer(timer)">
          <svg
            width="10"
            height="20"
            viewBox="0 0 10 20"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <rect x="7" width="3" height="20" fill="currentColor" />
            <rect width="3" height="20" fill="currentColor" />
          </svg>
        </button>
        <button class="square" @click="resetTimer(timer)">
          <svg
            width="20"
            height="20"
            viewBox="0 0 20 20"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <rect width="20" height="20" fill="currentColor" />
          </svg>
        </button>
      </div>
    </div>
    <button class="buttonAddNew" @click="addTimer">
      <svg
        width="20"
        height="20"
        viewBox="0 0 20 20"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect x="8.5" width="3" height="20" fill="#9E9E9E" />
        <rect
          y="11.5"
          width="3"
          height="20"
          transform="rotate(-90 0 11.5)"
          fill="#9E9E9E"
        />
      </svg>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timers: [],
    }
  },
  methods: {
    addTimer() {
      this.timers.push({ seconds: 0, running: false, timerId: null })
    },
    startTimer(timer) {
      timer.running = true
      timer.timerId = setInterval(() => {
        timer.seconds++
      }, 1000)
    },
    pauseTimer(timer) {
      timer.running = false
      clearInterval(timer.timerId)
    },
    resetTimer(timer) {
      timer.running = false
      clearInterval(timer.timerId)
      timer.seconds = 0
    },
    removeTimer(index) {
      this.timers.splice(index, 1)
    },
    continueTimer(timer) {
      timer.running = true
      timer.timerId = setInterval(() => {
        timer.seconds++
      }, 1000)
    },
    formatTime(seconds) {
      const hours = Math.floor(seconds / 3600)
      const minutes = Math.floor((seconds % 3600) / 60)
      const remainingSeconds = seconds % 60
      return `${hours.toString().padStart(2, '0')}:${minutes
        .toString()
        .padStart(2, '0')}:${remainingSeconds.toString().padStart(2, '0')}`
    },
  },
}
</script>
