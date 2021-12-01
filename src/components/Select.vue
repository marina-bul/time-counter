<template>
  <div class="select-list">
    <div
      v-for="item in items"
      :key="item[propValue]"
      class="select-list-item"
      :class="{'item-active': activeIndex==item[propValue] }"
      @click="selectItem(item)"
    >
      {{item[propName]}}
    </div>
  </div>
</template>

<script>
export default {
  name: "Select",
  props: {
    items: {
      type: Array,
      default: () => {
        [];
      },
    },
    propName: {
      type: String,
    },
    propValue: {
      type: String,
    },
  },
  data() {
    return {
      selectedItemId: null,
      activeIndex: 0,
    };
  },

  methods: {
    selectItem(item) {
      this.activeIndex = item[this.propValue];
      this.selectedItemId = item[this.propValue];
      this.$emit("select", this.selectedItemId);
    },
  },
};
</script>

<style scoped>
.select-list {
  padding: 1rem;
  width: 50%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}

.select-list-item {
  padding: 10px;
  font-size: 18px;
  color: antiquewhite;
  background-color: #531319;
  border-radius: 10px;
  cursor: pointer;
}

.item-active {
  background-color: #d27c1f;
}
</style>
