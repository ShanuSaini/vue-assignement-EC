<template>
  <div class="toggle-input-wrapper">
    <p v-if="label">{{ label }}</p>
    <label class="toggle-wrapper">
      <button
        class="toggle-state"
        :class="modelValue ? 'toggle-on' : 'toggle-off'"
        @click="toggle"
      >
        <span>
          <img
            src="/images/icons/advanced-search-disabled.svg"
            v-show="!modelValue"
          />
          <img
            src="/images/icons/advanced-search-enabled.svg"
            v-show="modelValue"
          />
        </span>
      </button>
    </label>
  </div>
</template>

<script>
export default {
  name: 'ToggleInput',
  props: {
    modelValue: {
      type: Boolean,
      default: false
    },
    label: {
      type: String,
      default: ''
    }
  },
  methods: {
    toggle() {
      this.$emit('update:modelValue', !this.modelValue);
    }
  }
};
</script>

<style lang="scss">
.toggle-input-wrapper {
  display: inline-flex;
  align-items: center;
  p {
    font-size: 12px;
    color: #acacac;
    margin-right: 10px;
  }
  .toggle-wrapper {
    display: inline-flex;
  }
  .toggle-state {
    position: relative;
    width: 40px;
    height: 20px;
    border-radius: 12px;
    background-color: #ffffff;
    box-shadow: inset 0px 1px 4px rgba(0, 0, 0, 0.2);
    cursor: pointer;
    padding: 0;
    border: 0;
    span {
      width: 20px;
      height: 20px;
      background-color: #ffffff;
      box-shadow: 0px 1px 5px rgba(0, 0, 0, 0.2);
      border: 1px solid transparent;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      position: absolute;
      left: 0;
      top: 0;
      transition: transform 0.3s cubic-bezier(0.22, 0.61, 0.36, 1);
    }
    &.toggle-off {
      span {
        border-color: #d23333;
      }
    }
    &.toggle-on {
      span {
        border-color: #57c046;
        transform: translateX(20px);
      }
    }
  }
}
</style>
