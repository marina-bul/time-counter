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
  margin-bottom: 10px;
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

@media (max-width: 600px) {
  .select-list {
    max-height: 150px;
    flex-direction: column;
    justify-content: start;
    flex-wrap: nowrap;
    overflow: auto;
    overflow-x: hidden;
  }

  .select-list::-webkit-scrollbar {
    width: 7px;
    background-color: #f7f4f1;
  }

  .select-list::-webkit-scrollbar-track {
    background-color: #f7f4f1;
  }

  .select-list::-webkit-scrollbar-thumb {
    background-color: #d27c1f;
  }

  .select-list-item {
    margin-bottom: 0;
    text-align: center;
    background-color: transparent;
    border: none;
  }

  .item-active {
    background-color: #d27c1f;
  }
}
</style>
