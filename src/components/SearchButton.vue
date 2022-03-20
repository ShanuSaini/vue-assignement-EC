<template>
  <button :type="type" @click="buttonClicked">{{ buttonText }}</button>
</template>

<script>
export default {
  name: 'SearchButton',
  props: {
    type: {
      type: String,
      default: 'button'
    },
    buttonText: {
      type: String,
      default: 'Button'
    }
  },
  methods: {
    buttonClicked() {
      this.$emit('buttonClicked');
    }
  }
};
</script>

<style>
button {
  width: 120px;
  height: 40px;
  border-top-right-radius: 3px;
  border-bottom-right-radius: 3px;
  background-color: #57c046;
  font-size: 13px;
  font-weight: 600;
  color: #ffffff;
  border: 0;
  cursor: pointer;
}
</style>
