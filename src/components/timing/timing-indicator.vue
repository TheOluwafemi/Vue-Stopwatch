<template>
  <section>
    <div class="time">
      <h2>
        {{ hours | padZero }} : {{ minutes | padZero }} : {{ seconds | padZero }} :
        {{ hSeconds | padZero }}
      </h2>
    </div>

    <div class="buttons">
      <button v-if="!timerStarted" class="btn" @click="startTimer">Start</button>
      <button v-else class="btn" @click="stopTimer">Stop</button>
    </div>
  </section>
</template>

<script>
  export default {
    data() {
      return {
        hours: 0,
        minutes: 0,
        seconds: 0,
        hSeconds: 0, //hundreth of a second
        timerStarted: false,
        secondsInterval: null,
      };
    },

    filters: {
      padZero: function (value) {
        if (value < 10) return `0${value}`;
        return value;
      },
    },

    watch: {
      hSeconds(oldValue, newValue) {
        if (newValue === 99) {
          this.seconds++;
          this.hSeconds = 0;
        }
      },

      seconds(oldValue, newValue) {
        if (newValue === 59) {
          this.minutes++;
          this.seconds = 0;
        }
      },

      minutes(oldValue, newValue) {
        if (newValue === 59) {
          this.hours++;
          this.minutes = 0;
          this.seconds = 0;
        }
      },
    },

    methods: {
      startTimer() {
        this.timerStarted = true;
        this.secondsInterval = setInterval(() => {
          this.hSeconds++;
        }, 10);
      },

      stopTimer() {
        clearInterval(this.secondsInterval);
        this.resetTimer();
        this.timerStarted = false;
      },

      resetTimer() {
        this.hSeconds = 0;
        this.seconds = 0;
        this.minutes = 0;
        this.hours = 0;
      },
    },

    beforeDestroy() {
      clearInterval(this.secondsInterval);
    },
  };
</script>

<style lang="scss" scoped>
  .time {
    font-size: 4rem;
    margin-bottom: 2rem;
  }

  .buttons {
    .btn {
      font-size: 2rem;
      outline: none;
      background: none;
      color: #c8c8c8;
      border: none;
      cursor: pointer;
      text-transform: uppercase;

      &:hover {
        color: #fff;
      }
    }
  }
</style>
