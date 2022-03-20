<template>
  <input
    type="text"
    :value="modelValue"
    @keydown="updateValue"
    placeholder="What you're looking for?"
  />
</template>

<script>
export default {
  name: 'TextInput',
  props: {
    modelValue: {
      type: String,
      default: ''
    }
  },
  methods: {
    updateValue(event) {
      this.$emit('update:modelValue', event.target.value);
    }
  }
};
</script>

<style scoped lang="scss">
input {
  height: 40px;
  width: 100%;
  padding: 0px 8px;
  border: 1px solid #acacac;
  border-right: 0;
  border-top-left-radius: 4px;
  border-bottom-left-radius: 4px;
  background-color: #ffffff;
  font-size: 14px;
  color: #121212;
  outline: none;
  &:focus {
    border-color: #acacac;
  }
  &::-webkit-input-placeholder {
    color: #cccccc;
  }
  &::-moz-placeholder {
    color: #cccccc;
  }
  &:-ms-input-placeholder {
    color: #cccccc;
  }
  &:-moz-placeholder {
    color: #cccccc;
  }
}
</style>
