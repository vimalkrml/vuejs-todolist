<script>
export default {
  props: ["show", "item"],
  methods: {
    onSubmit(e, id) {
      console.log(e);
      this.$emit("onEdit", e, id);
    },
  },
  data() {
    return {
      toggle: false,
    };
  },
};
</script>

<template>
  <div>
    <form
      @submit.prevent="onSubmit($event, item.id)"
      v-show="show"
      class="mb-2 bg-blue-400 rounded-md p-7 absolute top-[35%] right-[35%]"
    >
      <div class="mb-2 flex flex-col">
        <label>Name:</label>
        <input type="text" name="name" v-model="item.name" />
      </div>
      <div class="mb-2 flex flex-col">
        <label>username:</label>
        <input type="text" name="username" v-model="item.username" />
      </div>
      <div class="flex flex-col mb-2">
        <label>Email:</label>
        <input type="email" name="email" v-model="item.email" />
      </div>
      <div class="flex justify-center">
        <button @click="toggle = !toggle" class="rounded-md bg-white px-2">
          Save
        </button>
      </div>
    </form>
  </div>
</template>