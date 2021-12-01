<template>
  <div
    class="countdown"
    v-bind:style="{backgroundImage: `url(${background})`}"
  >
    <h2><span class="holiday">{{name}}</span> наступит через...</h2>

    <div class="countdown-container">
      <div class="countdown-el days-c">
        <p
          class="big-text"
          id="days"
        >{{formatTime(days)}}</p>
        <span>дней</span>
      </div>
      <div class="countdown-el hours-c">
        <p
          class="big-text"
          id="hours"
        >{{formatTime(hours)}}</p>
        <span>часов</span>
      </div>
      <div class="countdown-el minutes-c">
        <p
          class="big-text"
          id="minutes"
        >{{formatTime(minutes)}}</p>
        <span>минут</span>
      </div>
      <div class="countdown-el seconds-c">
        <p
          class="big-text"
          id="seconds"
        >{{formatTime(seconds)}}</p>
        <span>секунд</span>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  props: {
    date: {
      type: String,
      default: "01-01-2022",
    },
    name: {
      type: String,
      default: "Новый Год",
    },
    background: {
      type: String,
      default:
        "https://images.unsplash.com/photo-1610902277153-9fbd44104299?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
    },
  },

  data() {
    return {
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
      timer: null,
    };
  },

  mounted() {
    this.timer = setInterval(() => {
      this.countDown();
    }, 1000);
  },

  methods: {
    countDown() {
      const newYearsDate = new Date(this.date);
      const currentDate = new Date();

      let totalSeconds = (newYearsDate - currentDate) / 1000;

      this.days = Math.floor(totalSeconds / 3600 / 24);
      this.hours = Math.floor((totalSeconds / 3600) % 24);
      this.minutes = Math.floor((totalSeconds / 60) % 60);
      this.seconds = Math.floor(totalSeconds % 60);
    },

    formatTime(time) {
      return time < 10 ? `0${time}` : time;
    },
  },
};
</script>

<style scoped>
.countdown {
  position: relative;
  height: 100vh;
  padding-top: 15rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: "Poppins", sans-serif;
  color: antiquewhite;
  background-repeat: no-repeat;
  background-size: cover;
}
h2 {
  font-size: 5rem;
  letter-spacing: 0.5rem;
  text-align: center;
  text-shadow: -5px -3px 0 #222, 4px -4px 0 #222, -4px 4px 0 #222,
    4px 4px 0 #222, 5px 5px 0 antiquewhite, 6px 6px 0 antiquewhite,
    7px 7px 0 antiquewhite, 8px 8px 0 antiquewhite;
  letter-spacing: 10px;
  transform: scaleY(0.7);
  -webkit-transform: scaleY(0.7);
  -moz-transform: scaleY(0.7);
}

.countdown-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.big-text {
  margin: 1rem 3rem;
  font-size: 7rem;
  line-height: 1;
  font-weight: bold;
  text-shadow: -5px -3px 0 #222, 4px -4px 0 #222, -4px 4px 0 #222,
    4px 4px 0 #222, 5px 5px 0 antiquewhite, 6px 6px 0 antiquewhite,
    7px 7px 0 antiquewhite, 8px 8px 0 antiquewhite;
  letter-spacing: 10px;
  transform: scaleY(0.7);
  -webkit-transform: scaleY(0.7);
  -moz-transform: scaleY(0.7);
}

.countdown-el {
  text-align: center;
}

.countdown-el span {
  font-size: 1.3rem;
  text-shadow: 2px 2px 0 #222;
  letter-spacing: 10px;
}

@media (max-width: 900px) {
  h2 {
    font-size: 3rem;
    line-height: 5rem;
  }

  .big-text {
    font-size: 4rem;
  }
}

@media (max-width: 400px) {
  h2 {
    font-size: 2rem;
    line-height: 4rem;
    text-shadow: -3px -3px 0 #222, 4px -4px 0 #222, -4px 4px 0 #222,
      2px 2px 0 #222, 4px 4px 0 antiquewhite, 5px 5px 0 antiquewhite,
      6px 6px 0 antiquewhite, 7px 7px 0 antiquewhite;
  }

  .big-text {
    font-size: 3rem;
    text-shadow: -3px -3px 0 #222, 4px -4px 0 #222, -4px 4px 0 #222,
      2px 2px 0 #222, 4px 4px 0 antiquewhite, 5px 5px 0 antiquewhite,
      6px 6px 0 antiquewhite, 7px 7px 0 antiquewhite;
  }
}
</style>
