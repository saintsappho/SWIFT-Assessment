<template>
  <button @click="onClick" :style="{ background: color }" class="btn">{{ text }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String,
    color: String,
    onClick: {
      type: Function,
      default: () => console.log('Clicked')
    }
  },
  methods: {
    handleClick() {
      this.onClick();
    }
  }
};
</script>

<style scoped>
.btn {
  padding: 10px;
  border: none;
  cursor: pointer;
}
</style>
