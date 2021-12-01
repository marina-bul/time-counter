<template>
  <div class="header">
    <button @click="iconClick"></button>
  </div>
</template>

<script>
export default {
  name: "Icon",
  props: {},
  data() {
    return {};
  },
  methods: {
    iconClick() {
      this.$emit("showEvents");
    },
  },
};
</script>

<style scoped>
.header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 15px;
  text-align: right;
  background-color: #8b2030;
  z-index: 1;
}

button {
  width: 3rem;
  height: 3rem;
  background-image: url("../assets/time-and-date.png");
  background-repeat: no-repeat;
  background-size: cover;
  cursor: pointer;
}

@media (min-width: 768px) {
  button {
    width: 5rem;
    height: 5rem;
  }
}
</style>
