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
    // allow for custom and dynmamic click events
    handleClick() {
      this.onClick();
    }
  }
};
</script>

