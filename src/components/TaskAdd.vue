<script>
export default {
  data() {
    return {
      toggle: false,
      name: "",
      username: "",
      email: "",
    };
  },
  methods: {
    onSubmit(e) {
      this.$emit("onAdd", e);
    },
    // resetDefault() {
    //   this.name = "";
    //   this.username = "";
    //   this.email = "";
    // },
  },
};
</script>

<template>
  <div>
    <button
      @click="toggle = !toggle"
      class="
        px-1
        py-1
        text-white
        bg-slate-600
        hover:bg-black
        w-20
        mx-auto
        rounded-md
        mb-5
      "
    >
      Add Task
    </button>
    <form
      v-show="toggle"
      @submit="onSubmit"
      class="
        flex flex-col
        lg:flex-row lg:justify-between
        gap-5
        border-2
        p-2
        mb-5
        border-sky-300
        bg-gray-200
      "
    >
      <div class="flex flex-col lg:flex-row">
        <label for="" class="mr-2">Name</label>
        <input
          v-model="name"
          type="text"
          name="name"
          class="border rounded-md px-2 py-1"
        />
      </div>
      <div class="flex flex-col lg:flex-row">
        <label for="" class="mr-2">Username</label>
        <input
          v-model="username"
          type="text"
          name="username"
          class="border rounded-md px-2 py-1"
        />
      </div>
      <div class="flex flex-col lg:flex-row">
        <label for="" class="mr-2">Email</label>
        <input
          v-model="email"
          type="email"
          name="email"
          class="border rounded-md px-2 py-1"
        />
      </div>
      <button
        @click="toggle = !toggle"
        class="
          px-1
          w-16
          mx-auto
          text-white
          bg-gray-500
          hover:bg-blue-500
          rounded-md
        "
      >
        Add
      </button>
    </form>
  </div>
</template>
