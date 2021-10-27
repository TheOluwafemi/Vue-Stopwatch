<template>
  <section>
    <div>
      <h2 class="time">{{ hour }} : {{ minute }} : {{ seconds }}</h2>

      <button v-if="!timerStarted" class="btn" @click="startTimer">Start</button>
      <button v-else class="btn">Stop</button>
    </div>
  </section>
</template>

<script>
  export default {
    data() {
      return {
        hour: 0,
        minute: 0,
        seconds: 0,
        timerStarted: false,
      };
    },

    methods: {
      startTimer() {
        this.timerStarted = true;
        setInterval(() => {
          
          this.seconds++;
        }, 1000);
      },
    },
  };
</script>

<style lang="scss" scoped>
  .time {
    font-size: 70px;
  }

  .btn {
    font-size: 40px;
  }
</style>
