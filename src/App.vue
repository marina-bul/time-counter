<template>
  <div id="app">
    <header-icon
      v-show="!pickerIsActive"
      @showEvents="showPicker"
    />
    <transition name="fade">
      <date-picker
        v-show="pickerIsActive"
        @setHoliday="runTimer"
      />
    </transition>
    <timer
      :date="selectedHoliday.date"
      :name="selectedHoliday.name"
      :background="selectedHoliday.background"
    />
  </div>
</template>

<script>
import timer from "./components/timer.vue";
import DatePicker from "./components/DatePicker.vue";
import HeaderIcon from "./components/HeaderIcon.vue";
export default {
  components: {
    timer,
    DatePicker,
    HeaderIcon,
  },
  data() {
    return {
      selectedHoliday: {},
      pickerIsActive: false,
    };
  },

  methods: {
    runTimer(holiday) {
      this.selectedHoliday = holiday;
      this.pickerIsActive = false;
    },
    showPicker() {
      this.pickerIsActive = true;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  min-height: 100vh;
  background-color: darkblue;
  overflow: hidden;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 1s ease-in-out;
}

.fade-enter {
  transform: translateY(-100%);
}

.fade-leave {
  transform: translateY(0%);
}
</style>
