<script>
export default {
  props: ["show"],
  methods: {
    onClose() {
      this.$emit("onClose");
    },
  },
};
</script>

<template>
  <div @click="onClose" v-show="show">
    <slot></slot>
  </div>
</template>