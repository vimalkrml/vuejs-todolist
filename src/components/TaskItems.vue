<script>
import TaskEdit from "./TaskEdit.vue";
export default {
  props: ["item"],
  emits: ["onDelete", "onShow"],
  components: {
    TaskEdit,
  },
};
</script>

<template>
  <div
    class="
      p-1
      flex
      justify-between
      border-b
      mb-2
      border-sky-200
      bg-gray-200
      hero
      rounded
    "
  >
    <div>
      <slot></slot>
    </div>
    <div>
      <div>
        <slot name="action"></slot>
      </div>
    </div>
  </div>
</template>