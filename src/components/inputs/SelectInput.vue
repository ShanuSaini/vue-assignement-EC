<template>
  <div class="select-input-wrapper">
    <label class="input-label" v-if="label">{{ label }}</label>
    <div class="select-wrapper" :class="{ 'menu-open': isMenuOpened }">
      <div
        class="selected-item"
        :class="{ 'placeholder-style': !modelValue }"
        @click="toggleMenuOpen"
      >
        <span class="selected-item-text">
          {{ modelValue ? getSelectedItemText(modelValue) : 'Select Item' }}
        </span>
        <img src="/images/icons/select-input-arrow.svg" />
      </div>
      <div class="select-items">
        <div
          class="select-item"
          v-for="item in items"
          :key="item.value"
          @click="selectValue(item.value)"
        >
          {{ item.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ToggleInput',
  props: {
    modelValue: {
      type: String,
      default: ''
    },
    items: {
      type: Array,
      required: true
    },
    label: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      isMenuOpened: false
    };
  },
  methods: {
    toggleMenuOpen() {
      this.isMenuOpened = !this.isMenuOpened;
    },
    selectValue(value) {
      this.toggleMenuOpen();
      this.$emit('update:modelValue', value);
    },
    getSelectedItemText(value) {
      const selectedItem = this.items.filter(item => {
        if (item.value === value) return true;
      });
      return selectedItem[0].text;
    }
  }
};
</script>

<style scoped lang="scss">
.select-wrapper {
  cursor: pointer;
  position: relative;
}
.selected-item {
  height: 40px;
  display: flex;
  align-items: center;
  width: 100%;
  padding: 0px 8px;
  border: 1px solid #cccccc;
  border-radius: 4px;
  background-color: #ffffff;
  background-size: cover;
  font-size: 14px;
  justify-content: space-between;
  &.placeholder-style {
    color: #a9a9a9;
  }
}
.selected-item-text {
  max-width: calc(100% - 20px);
  overflow: hidden;
  text-overflow: ellipsis;
}

.select-items {
  background-color: #fff;
  border-bottom-left-radius: 4px;
  border-bottom-right-radius: 4px;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
  position: absolute;
  width: 100%;
  display: none;
}
.menu-open {
  .selected-item {
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  .select-items {
    display: block;
  }
}
.select-item {
  padding: 10px 8px;
  border-bottom: 1px solid #cccccc;
  font-size: 14px;
  line-height: 19px;
  color: #121212;
  &:last-child {
    border: 0;
  }
}
</style>
