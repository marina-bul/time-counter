<template>
  <form
    class="date-form"
    @submit.prevent
  >
    <holyday-select
      :items="items"
      :prop-name="'name'"
      :prop-value="'id'"
      @select="setHolidayId"
    />
    <button @click="setHoliday">Запустить таймер</button>
    <!-- <button>Добавить событие</button> -->
  </form>
</template>

<script>
import HolydaySelect from "./Select.vue";
import holidays from "../assets/holidays.json";
export default {
  components: {
    HolydaySelect,
  },

  data() {
    return {
      items: holidays,
      holidayId: null,
    };
  },

  methods: {
    setHoliday() {
      const holiday = this.items.find((el) => el.id == this.holidayId);
      this.$emit("setHoliday", holiday);
    },

    setHolidayId(id) {
      this.holidayId = id;
    },
  },
};
</script>

<style scoped>
.date-form {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 15px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: #fff;
  background-color: #8b2030;
  z-index: 1;
}

button {
  margin-top: 20px;
  padding: 10px;
  color: antiquewhite;
  background-color: #d27c1f;
  border-radius: 10px;
  border: none;
  outline: none;
  cursor: pointer;
}
</style>
