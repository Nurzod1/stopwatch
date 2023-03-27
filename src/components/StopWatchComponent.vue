<template>
  <div class="stopwatch" :class="{ active: running }">
    <p class="stopwatch-text">
      {{ timerText }}
    </p>
    <hr class="stopwatch-line" :class="{ active: running }" />
    <div class="stopwatch-btn__group">
      <button
        class="stopwatch-btn"
        :class="{ active: running }"
        @click="toggleHandler"
        v-html="toggleIcon"
      />
      <button
        class="stopwatch-btn"
        :class="{ active: running }"
        @click="resetHandler"
      >
        <svg
          width="20"
          height="20"
          viewBox="0 0 20 20"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <rect width="20" height="20" fill="white" />
        </svg>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "StopWatchComponent",
  data() {
    return {
      timer: null,
      seconds: 0,
      minutes: 0,
      hour: 0,
      running: false,
    };
  },
  computed: {
    secondNum() {
      if (this.seconds <= 9) {
        return `0${this.seconds}`;
      } else {
        return this.seconds;
      }
    },
    minutesNum() {
      if (this.minutes <= 9) {
        return `0${this.minutes}`;
      } else {
        return this.minutes;
      }
    },
    hourNum() {
      if (this.hour <= 9) {
        return `0${this.hour}`;
      } else {
        return this.hour;
      }
    },
    timerText() {
      if (this.hour) {
        return `${this.hourNum}:${this.minutesNum}:${this.secondNum}`;
      }
      if (this.minutes) {
        return `${this.minutesNum}:${this.secondNum}`;
      }
      return this.secondNum;
    },
    toggleIcon() {
      if (this.running) {
        return `<svg
          width="10"
          height="20"
          viewBox="0 0 10 20"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <rect x="7" width="3" height="20" fill="white" />
          <rect width="3" height="20" fill="white" />
        </svg>`;
      }
      return `<svg
          width="17"
          height="20"
          viewBox="0 0 17 20"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path d="M0 20V0L17 10L0 20Z" fill="#9e9e9e" />
        </svg>`;
    },
  },
  methods: {
    toggleHandler() {
      console.log("start", this.running);
      this.running = !this.running;
      this.timer && clearInterval(this.timer);

      if (!this.running) {
        return;
      }

      this.timer = setInterval(() => {
        this.addHandler();
      }, 10);
    },
    resetHandler() {
      this.running = false;
      this.timer && clearInterval(this.timer);
      this.seconds = 0;
      this.minutes = 0;
      this.hour = 0;
    },
    addHandler() {
      this.seconds++;
      if (this.seconds == 60) {
        this.seconds = 0;
        this.minutes++;
        if (this.minutes == 60) {
          this.minutes = 0;
          this.hour++;
        }
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.stopwatch {
  width: 225px;
  height: 120px;
  background-color: #696969;
  color: #9e9e9e;
  display: flex;
  flex-direction: column;
  gap: 20px;
  justify-content: center;

  &.active {
    color: #ffffff;
  }

  &-btn {
    width: 20px;
    height: 20px;

    svg {
      rect {
        fill: #9e9e9e;
      }

      path {
        fill: #9e9e9e;
      }
    }

    &.active {
      svg {
        rect {
          fill: #ffffff;
        }

        path {
          fill: #ffffff;
        }
      }
    }

    &__group {
      display: flex;
      gap: 10px;
      justify-content: center;
    }
  }

  &-line {
    height: 1px;
    border: none;
    background-color: #9e9e9e;

    &.active {
      background-color: #ffffff;
    }
  }
}
</style>